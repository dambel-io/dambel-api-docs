# POST /api/v1/payments/deposit

Creates a deposit request for the authenticated user to add funds to their account.


---

## Permissions
| Permission           | Description                        |
|----------------------|------------------------------------|
| `payments.view_own`  | Access the payment system          |
| `payments.deposit`   | Deposit money into own account     |

---

## Request Body Parameters
| Name        | Type    | Required | Description                                                    | Example         |
|-------------|---------|----------|----------------------------------------------------------------|-----------------|
| amount      | decimal | Yes      | Amount to credit, in Tooman. Minimum 1                         | 700000          |
| description | string  | No       | Description for the deposit (max 2000 characters)              | "Top-up"        |

`amount` is what the user's balance is credited with. The gateway's fee is charged **on top** of
it, so the figure the user actually pays is `payable_amount` — see
[the gateway fee](../../payments.md#currency-and-the-gateway-fee).

---

## Request Example
```json
{
  "amount": 700000,
  "description": "Top-up"
}
```

---

## Response

### 201 Created
Returns a payment gateway link for the user to complete the deposit process, along with the
amounts involved. All amounts are in Tooman, and `amount + gateway_fee == payable_amount`.

| Field          | Type   | Description                                                     |
|----------------|--------|-----------------------------------------------------------------|
| link           | string | Gateway URL to redirect the user to                             |
| amount         | number | Amount the user's balance will be credited with                 |
| gateway_fee    | number | Gateway fee the user pays on top of `amount`                    |
| payable_amount | number | Total the user is charged at the gateway                        |

#### Example
```json
{
  "link": "https://gateway.zibal.ir/start/123456789",
  "amount": 700000,
  "gateway_fee": 7786,
  "payable_amount": 707786
}
```

---

### Double submission

A repeated request with the same `amount` and `description` from the same user **reuses the
existing unfinalized deposit** rather than creating a second one, for **300 seconds** after the
first. The response is a `201` carrying that payment's gateway link, so a client that retries —
because the user double-tapped, or the first response was lost — does not strand a second
pending payment on the account.

Once the window passes, or once the first deposit is finalized (`is_done`), an identical request
creates a new payment. A deposit with a different `amount` or `description` is always new.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 500    | Payment service provider error (`{ "message": "Payment service provider error.", "error": "..." }`) | N/A |
| 422    | Validation error           | [Validation error](../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
