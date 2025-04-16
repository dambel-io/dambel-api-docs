# `GET /api/v1/gyms/{gym-id}/buffet-items`
You can get list of the buffet items of a gym using this API.


## Params

No parameter.

## Response

### 200 OK

```json
{
    "data": [<gym buffet item resource>, ...],
}
```

[Gym Buffet Item Resource](../../resources/gym_buffet_item.md)

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)

### 404 Not Found
[Not-found error](../../not-found-errors.md)
