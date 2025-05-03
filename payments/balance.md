# `GET /api/v1/payments/balance`
Users can see their balance using this API.


## Permissions

- `payments.view_own`: To access the payment system
- `payments.view_own_balance`: To view their own balance

## Response

### 200 OK
```json
{
    "balance": 123.456,
}
```

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)
