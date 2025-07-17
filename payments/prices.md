# GET /api/v1/payments/prices

Retrieves general data for premium plan prices, commission rates, and boost plans in the platform.


---

## Permissions
| Permission           | Description                        |
|----------------------|------------------------------------|
| `payments.view_own`  | Access the payment system          |
| `payments.view_prices`| View prices and commission rates   |

---

## Response

### 200 OK
Returns platform pricing and commission data.

#### Example
```json
{
  "gym_commission_rate": 0.02,
  "premium_plans": {
    "plus": {
      "monthly_price": 50000,
      "discount": 0,
      "yearly_price_discount": 0.85,
      "role": "user_plus"
    }
  },
  "boosts": {
    "basic": {
      "price": 60000,
      "duration": 7,
      "level": 1
    },
    "pro": {
      "price": 150000,
      "duration": 14,
      "level": 2
    }
  }
}
```

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
