# POST /api/v1/payments/verify-store-purchase

Grants what a purchase an app store's in-app billing has already settled bought — a Premium
subscription or a marketing boost, depending on the SKU.

Store policy requires a digital good consumed inside the app to be sold through the store's own
billing on a store build, so a Bazaar build cannot top up its Dambel wallet and spend it on one.
It buys the SKU in the store and posts the resulting purchase token here. The token is validated
against the store's API server-side before anything is granted — a client reporting that the
purchase succeeded is never sufficient on its own.

**Dambel's own digital goods only.** Gym subscriptions and training-service purchases are
real-world services, exempt from store billing, and carry Dambel's own platform commission — they
settle through the wallet and Zibal and must never be sent here. See
[Payments](../../payments.md#store-billing-cafe-bazaar).


Rate limited to 10 requests per minute, because every call that is not a replay makes an outbound
request to the store.

---

## Permissions
| Permission                             | Description                                    |
|----------------------------------------|------------------------------------------------|
| `payments.view_own`                    | Access the payment system                      |
| `payments.buy_premium`                 | Required for a **Premium** SKU                 |
| `payments.boost_own` / `boost_all`     | Required for a **boost** SKU, on that target   |

The SKU decides which product is being bought, so it decides which permission applies. The route
gate is the union — a caller holding neither is refused before the body is read — and the endpoint
then re-checks the one that actually applies, exactly as
[`POST /payments/buy-premium`](buy-premium.md) and [`POST /payments/boost`](boost.md) do for the
wallet rail. Holding one does not buy the other.

---

## Request Body Parameters
| Name           | Type   | Required   | Description                                                                                       | Example          |
|----------------|--------|------------|---------------------------------------------------------------------------------------------------|------------------|
| channel        | string | Yes        | The store that settled the purchase. Currently only `bazaar`. `direct` is rejected — it is the wallet, and there is no store purchase to verify. | "bazaar"         |
| product_id     | string | Yes        | The store SKU that was bought, max 191 characters.                                                | "premium_plus"   |
| purchase_token | string | Yes        | The purchase token the store's SDK returned to the client, max 255 characters.                    | "AbC123…"        |
| boostable_type | string | Boost SKUs | What is being boosted: `gym` or `training_service`. Required for a boost SKU, ignored otherwise.  | "gym"            |
| boostable_id   | int    | Boost SKUs | ID of the gym or training service to boost. Required for a boost SKU, ignored otherwise.          | 42               |

A boost is the one product whose purchase needs a target: Premium is granted to the buyer, but a
boost is granted to a gym or a training service they name. Sending a boost SKU without a target is
a `422` naming both fields.

### The SKUs Bazaar sells

| SKU              | Grants                                       | Console price |
|------------------|----------------------------------------------|---------------|
| `premium_plus`   | One month of the `plus` premium plan          | 19,990,000 Rial |
| `boost_basic`    | The `basic` boost on the named target         | 990,000 Rial    |
| `boost_pro`      | The `pro` boost on the named target           | 1,900,000 Rial  |

These are configured in `config/monetization.php` under `channels.<channel>.products`, and the keys
must match the product IDs registered in the Bazaar developer console exactly. Bazaar's validation
API returns no amount, so the console price and the configured price are kept in step by hand.
The map is deliberately not published by [`GET /payments/prices`](prices.md); the client knows its
own SKUs from the store SDK.

There is no yearly Premium SKU — the console sells `premium_plus` as a single one-off month.

---

## Request Examples

Premium:
```json
{
  "channel": "bazaar",
  "product_id": "premium_plus",
  "purchase_token": "AbC123DeF456"
}
```

A boost:
```json
{
  "channel": "bazaar",
  "product_id": "boost_basic",
  "purchase_token": "AbC123DeF456",
  "boostable_type": "gym",
  "boostable_id": 42
}
```

---

## Response

### 201 Created
The token was validated and the SKU's grant was made. A Premium SKU returns the created
subscription; a boost SKU returns the created boost.

#### Example — Premium
```json
{
  "data": {
    "id": 1,
    "user_id": 42,
    "type": "plus",
    "starts_at": "2026-09-08 12:00:00",
    "expires_at": "2026-10-08 12:00:00"
  }
}
```

For a full schema, see [User Premium Subscription Resource](user_premium_subscription_resource.md).

#### Example — a boost
```json
{
  "data": {
    "id": 101,
    "boostable_type": "App\\Models\\Gyms\\Gym",
    "boostable_id": 42,
    "level": 1,
    "starts_at": "2026-09-09 12:00:00",
    "ends_at": "2026-09-16 12:00:00"
  }
}
```

For a full schema, see [Marketing Boost Resource](marketing_boost_resource.md).

---

### 200 OK
This purchase token has already been redeemed. Whatever it granted is returned unchanged
and **nothing new is created** — no second subscription, no second boost, no second payment row.

The body is identical in shape to the 201 for that SKU. **The status code is the only way to tell a
fresh grant from a replay**, so a client that treats any 2xx as success behaves correctly.

---

### Idempotency
A client retry, a redelivered callback and the store's own "restore purchases" all arrive as the
same purchase token, and none of them may grant twice. The token is looked up in the
`store_purchases` ledger before the store is contacted, so a replay is cheap and never bills an API
call. Under a genuine race the unique index on `(channel, purchase_token)` is the guarantee: the
second attempt rolls its whole grant back and is then answered from the ledger like any other
replay — `200` for the token's owner, `404` for anyone else. A race never surfaces as a `500`.

A token belongs to whoever first redeemed it. Presenting someone else's token returns the same
`404` an unknown product does, so a refusal cannot be used to discover that a token exists.

### What is recorded
A store purchase brings no money into the Dambel wallet — the store holds it and settles out of
band. It is booked as a `store_purchase` payment row, which appears in payment history and in the
finance reports but is **excluded from the balance**, so a user's spendable balance is unchanged by
buying Premium or a boost in a store. See
[how the balance is computed](../../payments.md#how-the-balance-is-computed).

The `store_purchases` receipt records which grant the SKU made: `user_premium_subscription_id` for
a Premium SKU, `marketing_boost_id` for a boost SKU. Exactly one of the two is set.

### Check before you buy
The store takes the money before this endpoint is ever called, so a refusal here means the user has
paid and received nothing — a support refund is then the only remedy. Two refusals are foreseeable
and a client **must** rule them out before it starts the store's purchase flow:

- **Premium** — the user already has an active subscription (`400`).
- **A boost** — the target already carries a live boost (`400`).

---

### Error Responses
| Status | Description                                                       | Reference                                              |
|--------|-------------------------------------------------------------------|--------------------------------------------------------|
| 400    | Premium SKU: the user already has an active subscription          | N/A                                                    |
| 400    | Boost SKU: the target already carries a live boost                | N/A                                                    |
| 400    | The store did not confirm the purchase (canceled, pending, or a response the server cannot read) | N/A                          |
| 404    | Unknown product for this channel, or a token redeemed by another user | [Not-found error](../_globals/not-found-errors.md) |
| 404    | Boost SKU: the named gym or training service does not exist       | [Not-found error](../_globals/not-found-errors.md)     |
| 422    | Validation error, including an unknown channel or `direct`, or a boost SKU with no target | [Validation error](../_globals/validation-errors.md) |
| 429    | Rate limited                                                      | [Rate-limit error](../_globals/rate-limit-errors.md)   |
| 500    | The store could not be reached, or the grant failed after the store confirmed the purchase | [Server error](../_globals/server-errors.md) |
| 401    | Unauthorized                                                      | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Missing the permission this SKU needs — `payments.buy_premium` for Premium, `boost` on the target for a boost | [Permission error](../_globals/permission-errors.md) |

Everything the caller controls is refused **before** the store is contacted — an unknown SKU, a
missing target, a target that is not theirs. An unauthorized caller therefore cannot spend this
endpoint's outbound budget.

The two failure modes are different problems and carry different bodies. A **`400`** with
`store_purchase.verification_failed` means the store answered and said this is not a completed
purchase — retrying will not help. A **`500`** with `payments.provider_error` means we could not get
an answer out of the store at all, so a retry later may succeed; that is the same code and the same
message [`POST /payments/deposit`](deposit.md) returns when Zibal is unreachable.

Both of this endpoint's `500`s use the `{"error": "…"}` shape documented in
[Server error](../_globals/server-errors.md), so a client reads one key whichever failure it hit.
(`POST /payments/deposit` returns its provider error under `message`; that is its shipped contract
and is not changed by this endpoint matching the global instead.)
