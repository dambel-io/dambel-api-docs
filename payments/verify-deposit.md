# `GET /api/v1/payments/verify-deposit/{deposit-id}`
This is the callback for payment service provider to verify the deposit.


## Params

- `Authority`: From PSP
- `Status`: From PSP

## Response

### 200 OK
```json
{
    "message": "Deposit successful",
    "payment": <payment resource>
}
```

[Payment Resource](payment_resource.md)

### 400 Bad Request
When payment fails

```json
{
    "error": "..."
}
```
