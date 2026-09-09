# POST /api/v1/payments/verify-store-purchase

Grants a Premium subscription from a purchase an app store's in-app billing has already settled.

Store policy requires a digital good consumed inside the app to be sold through the store's own
billing on a store build, so a Bazaar build cannot top up its Dambel wallet and spend it on
Premium. It buys the SKU in the store and posts the resulting purchase token here. The token is
validated against the store's API server-side before anything is granted — a client reporting that
the purchase succeeded is never sufficient on its own.

**Premium only.** Gym subscriptions and training-service purchases are real-world services, exempt
from store billing, and carry Dambel's own platform commission — they settle through the wallet and
Zibal and must never be sent here. See [Payments](../../payments.md#store-billing-cafe-bazaar).


Rate limited to 10 requests per minute, because every call that is not a replay makes an outbound
request to the store.

---

## Permissions
| Permission             | Description                          |
|------------------------|--------------------------------------|
| `payments.view_own`    | Access the payment system            |
| `payments.buy_premium` | Buy a premium account                |

The same permission as [`POST /payments/buy-premium`](buy-premium.md): it is the same product being
bought, settled by a different rail.

---

## Request Body Parameters
| Name           | Type   | Required | Description                                                                                       | Example             |
|----------------|--------|----------|---------------------------------------------------------------------------------------------------|---------------------|
| channel        | string | Yes      | The store that settled the purchase. Currently only `bazaar`. `direct` is rejected — it is the wallet, and there is no store purchase to verify. | "bazaar"            |
| product_id     | string | Yes      | The store SKU that was bought, max 191 characters.                                                | "premium_plus_1m"   |
| purchase_token | string | Yes      | The purchase token the store's SDK returned to the client, max 255 characters.                    | "AbC123…"           |

The SKUs a channel sells, and how many months of which plan each grants, are configured in
`config/monetization.php` under `channels.<channel>.products`. They are deliberately not published
by [`GET /payments/prices`](prices.md); the client knows its own SKUs from the store SDK.

---

## Request Example
```json
{
  "channel": "bazaar",
  "product_id": "premium_plus_1m",
  "purchase_token": "AbC123DeF456"
}
```

---

## Response

### 201 Created
The token was validated and a subscription was granted. Returns the created subscription.

#### Example
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

---

### 200 OK
This purchase token has already been redeemed. The subscription it granted is returned unchanged
and **nothing new is created** — no second subscription, no second payment row.

The body is identical in shape to the 201. **The status code is the only way to tell a fresh grant
from a replay**, so a client that treats any 2xx as success behaves correctly.

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
buying Premium in a store. See [how the balance is computed](../../payments.md#how-the-balance-is-computed).

---

### Error Responses
| Status | Description                                                       | Reference                                              |
|--------|-------------------------------------------------------------------|--------------------------------------------------------|
| 400    | The user already has an active subscription                       | N/A                                                    |
| 400    | The store did not confirm the purchase (canceled, pending, or a response the server cannot read) | N/A                          |
| 404    | Unknown product for this channel, or a token redeemed by another user | [Not-found error](../_globals/not-found-errors.md) |
| 422    | Validation error, including an unknown channel or `direct`        | [Validation error](../_globals/validation-errors.md)   |
| 429    | Rate limited                                                      | [Rate-limit error](../_globals/rate-limit-errors.md)   |
| 500    | The store could not be reached, or the grant failed after the store confirmed the purchase | [Server error](../_globals/server-errors.md) |
| 401    | Unauthorized                                                      | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Missing `payments.buy_premium`                                    | [Permission error](../_globals/permission-errors.md) |

The two failure modes are different problems and carry different bodies. A **`400`** with
`store_purchase.verification_failed` means the store answered and said this is not a completed
purchase — retrying will not help. A **`500`** with `payments.provider_error` means we could not get
an answer out of the store at all, so a retry later may succeed; that is the same code and the same
message [`POST /payments/deposit`](deposit.md) returns when Zibal is unreachable.

Both of this endpoint's `500`s use the `{"error": "…"}` shape documented in
[Server error](../_globals/server-errors.md), so a client reads one key whichever failure it hit.
(`POST /payments/deposit` returns its provider error under `message`; that is its shipped contract
and is not changed by this endpoint matching the global instead.)
