# `POST /api/v1/payments/boost`
You can boost something using this API.


## Permissions

- `payments.boost_own`: To boost your own things
- `payments.boost_all`: To boost everything

## Params

- `boostable_type`: Boostable type:
    - `gym`
    - `training_service`
- `boostable_id`: Id of the boostable
- `plan`: Name of the boost plan

Use [`/prices`](prices.md) to get plans and prices.

## Response

### 201 Created
```json
<marketing boost resource>
```

[Marketing Boost Resource](marketing_boost.md)

### 400 Bad Request
When an unexpected error happens during the payment process.

```json
{
    "error": "You already have a boost"
}
```

```json
{
    "error": "Insufficient balance"
}
```

### 422 Unprocessable Entity
[Validation error](../_globals/validation-errors.md)

### 404 Not Found
```json
{
    "error": "Plan not found"
}
```

### 500 Internal Server Error
When there is an unexpected error:
```json
{
    "error": "Purchase failed"
}
```

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)
