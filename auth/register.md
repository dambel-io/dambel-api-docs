# `POST /api/v1/auth/register`
This API creates a new user.


## Params

- `email`: User email
- `phone`: User phone number (optional)
- `first_name`: First name of the user
- `last_name`: Last name of the user
- `password`: User password
- `referral_code`: Optional referral code

## Response

### 201 Created
```json
{
    "user": {<user resource>},
    "token": "<the API token will be set here>"
}
```

[User Resource](../users/user_resource.md)

[How to use API token?](login.md#how-to-use-api-token)

409:
```json
{
    "error": "Email address/phone number is already in use"
}
```

### 422 Unprocessable Entity
[Validation error](../_globals/validation-errors.md)

### 429 Too Many Requests
[Rate-limit error](../_globals/rate-limit-errors.md) (10 requests per minute is allowed)
