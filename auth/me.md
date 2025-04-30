# `GET /api/v1/auth/me`
This API will return the logged in user info.


## Params
Nothing.

## Response

### 200 OK


```json
{
    "data": <user resource>,
    "permissions": ["permission 1", "permission 2"]
}
```

[User Resource](../users/user_resource.md)

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)
