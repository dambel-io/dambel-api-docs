# POST /api/v1/payments/buy-premium

Purchases a premium account for the authenticated user.


---

## Permissions
| Permission           | Description                        |
|----------------------|------------------------------------|
| `payments.view_own`  | Access the payment system          |
| `payments.buy_premium`| Buy a premium account              |

---

## Request Body Parameters
| Name         | Type   | Required | Description                                                                 | Example         |
|--------------|--------|----------|-----------------------------------------------------------------------------|-----------------|
| plan         | string | Yes      | Name of the premium plan                                                    | "plus"         |
| months_count | int    | Yes      | Number of months (min 1, 12+ for discount)                                  | 12              |

Use [`/prices`](prices.md) to get plan names and discount rates.

---

## Request Example
```json
{
  "plan": "plus",
  "months_count": 12
}
```

---

## Response

### 201 Created
Returns the created user premium subscription resource.

#### Example
```json
{
  "id": 1,
  "user_id": 42,
  "plan": "plus",
  "starts_at": "2025-01-01 00:00:00",
  "expires_at": "2026-01-01 00:00:00"
}
```

For a full schema, see [User Premium Subscription Resource](user_premium_subscription_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 400    | Already subscribed/Insufficient balance | N/A                                 |
| 422    | Validation error           | [Validation error](../_globals/validation-errors.md) |
| 404    | Plan not found             | N/A                                            |
| 500    | Subscription failed        | N/A                                            |
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
