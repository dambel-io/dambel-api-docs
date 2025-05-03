# `POST /api/v1/payments/deposit`
You can deposit some money into your account using this API.


## Permissions

- `payments.view_own`: To access the payment system
- `payments.deposit`: To be able to deposit money into their own account

## Params

- `amount`: Required decimal
- `description`: An optional description for the deposit

## Response

### 201 Created
```json
{
    "link": "<link to the payment service provider gate way>",
}
```

User needs to be redirected to that link to complete the payment process.

### 400 Bad Request
When an unexpected error happens during the payment process.

```json
{
    "error": "..."
}
```

### 422 Unprocessable Entity
[Validation error](../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)
