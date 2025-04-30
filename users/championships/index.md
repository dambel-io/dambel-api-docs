# `GET /api/v1/users/{user-id}/championships`
You can get list of the championships of a user using this API.


## Params

No parameter.

## Response

### 200 OK

```json
{
    "data": [<championship resource>, ...],
}
```

[Championship Resource](championship_resource.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)
