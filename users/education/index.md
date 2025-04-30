# `GET /api/v1/users/{user-id}/education`
You can get list of the education of a user using this API.


## Params

No parameter.

## Response

### 200 OK

```json
{
    "data": [<education resource>, ...],
}
```

[Education Resource](education_resource.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)
