# `GET /api/v1/gyms/{gym-id}/equipment`
You can get list of the equipment of a gym using this API.


## Permissions

- `gyms.view_any`: is needed if you are trying to read list of equipment for an inactive gym

## Params

No parameter.

## Response

### 200 OK

```json
{
    "data": [<gym equipment resource>, ...],
}
```

[Gym Equipment Resource](../../resources/gym_equipment.md)

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)

### 404 Not Found
[Not-found error](../../not-found-errors.md)
