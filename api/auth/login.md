# `/api/v1/auth/login`
This API gives user the ability to login and receive an API token.

- Method: `POST`

### Params

- `email`: User email
- `password`: User password
- `expiration`: Token expiration. Should be an integer as seconds. It's **optional** and if you don't pass it, token will never expire
- `token_name`: An **optional** name for the token. If you don't set it, the user agent value will be used as the token name instead

### Response

201:
```json
{
    "token": "<the API token will be set here>"
}
```

403:
```json
{
    "error": "Invalid credentials"
}
```

422: [Validation error](../validation-errors.md)

429: [Rate-limit error](../rate-limit-errors.md) (10 requests per minute is allowed)

### How to use API token?
After you did the login and received the token, you should save it in the client side (for example in a cookie or local storage),
and then for every next API call you make, you should pass that token too.
You should pass it as a Bearer token in the **headers** this way:

```
Authorization: Bearer {token}
```
