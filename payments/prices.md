# `GET /api/v1/payments/prices`
You can get general data for premium plan prices and commission rates in the platform using this API.


## Response

### 200 OK

```json
{
    "gym_commission_rate": 0.02,
    "premium_plans": {
        "plus": {
            "monthly_price": 50000,
            "yearly_price_discount": 0.85,
            "role": "user_plus"
        }
    }
}
```

### 401 Unauthorized
[Authentication error](../authentication-errors.md)
