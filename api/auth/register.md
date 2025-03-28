# `POST /api/v1/auth/register`
This API creates a new user.


### Params

- `email`: User email
- `password`: User password
- `expiration`: Token expiration. Should be an integer as seconds. It's **optional** and if you don't pass it, token will never expire
- `token_name`: An **optional** name for the token. If you don't set it, the user agent value will be used as the token name instead

### Response

201:
```json
{
    "user": {<user resource>},
    "token": "<the API token will be set here>"
}
```

[User Resource](../resources/user.md)

[How to use API token?](login.md#how-to-use-api-token)

409:
```json
{
    "error": "Email address/phone number is already in use"
}
```

422: [Validation error](../validation-errors.md)

429: [Rate-limit error](../rate-limit-errors.md) (10 requests per minute is allowed)
