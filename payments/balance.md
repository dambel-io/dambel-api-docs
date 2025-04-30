# `GET /api/v1/payments/balance`
Users can see their balance using this API.


## Permissions

No specific permission is required. All users can get their own balance.

## Response

### 200 OK
```json
{
    "balance": 123.456,
}
```

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)
