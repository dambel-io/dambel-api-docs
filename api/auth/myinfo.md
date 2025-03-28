# `GET /api/v1/auth/myinfo`
This API will return the logged in user info.


### Params
Nothing.

### Response

200:

```json
{
    "data": <user resource>,
    "permissions": ["permission 1", "permission 2"]
}
```

[User Resource](../resources/user.md)

401: [Authentication error](../authentication-errors.md)
