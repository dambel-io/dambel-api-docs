# `GET /api/v1/gyms/{gym-id}/equipment`
You can get list of the equipment of a gym using this API.


## Permissions

- `gyms.view_all`: is needed if you are trying to read list of equipment for an inactive gym

## Params

No parameter.

## Response

### 200 OK

```json
{
    "data": [<gym equipment resource>, ...],
}
```

[Gym Equipment Resource](gym_equipment_resource.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)
