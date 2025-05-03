# `POST /api/v1/payments/buy-premium`
Users can purchase a premium account using this API.


## Permissions

- `payments.view_own`: To access the payment system
- `payments.buy_premium`: To be able to buy premium account

## Params

- `plan`: Name of the plan
- `months_count`: Number of the months. Minimum is 1. If you choose 12 or more, a discount will be applied

Use [`/prices`](prices.md) to get plan names and discount rates.

## Response

### 201 Created
```json
<user premium subscription resource>
```

[User Premium Subscription Resource](user_premium_subscription_resource.md)

### 400 Bad Request
When an unexpected error happens during the payment process.

```json
{
    "error": "You already have a subscription"
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
    "error": "Subscription failed"
}
```

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)
