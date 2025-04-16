# `GET /api/v1/users/{user-id}/training-services`
You can get list of the training services of a user using this API.


## Params

No parameter.

## Response

### 200 OK

```json
{
    "data": [<training service resource>, ...],
}
```

[Training Service Resource](../../resources/training_service.md)

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)

### 404 Not Found
[Not-found error](../../not-found-errors.md)
