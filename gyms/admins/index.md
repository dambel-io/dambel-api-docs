# `GET /api/v1/gyms/{gym-id}/admins`
You can get list of the subscription admins of a gym using this API.


## Permissions

- `gym_admins.view_own`: to view admins list for your own gym
- `gym_admins.view_all`: to view admins list for all of the gyms

## Params

No parameter.

## Response

### 200 OK

```json
{
    "data": [<gym admin resource>, ...],
}
```

[Gym Admin Resource](gym_admin_resource.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)
