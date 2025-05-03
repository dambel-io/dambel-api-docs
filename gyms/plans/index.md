# `GET /api/v1/gyms/{gym-id}/plans`
You can get list of the subscription plans of a gym using this API.


## Permissions

- `gyms.view_all`: is needed if you are trying to read list of plans for an inactive gym or seeing inactive plans

## Params

No parameter.

## Response

### 200 OK

```json
{
    "data": [<gym plan resource>, ...],
}
```

[Gym Plan Resource](gym_plan_resource.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)
