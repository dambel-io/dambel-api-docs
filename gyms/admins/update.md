# `PUT /api/v1/gyms/{gym-id}/admins/{admin-id}`
You can update a gym admin using this API.


## Permissions

- `gym_admins.update`: update gym admins of their own gyms
- `gym_admins.update_any`: update gym admins for any gym

## Params

- `title`: Title of the admin (optional, maxlength 255)
- `permissions`: List of the permission names as an array

All of the parameters are optional. If you don't pass them, they won't get updated.
You still can set them to null if you want.

## Response

### 200 OK

```json
<gym admin resource>
```

[Gym Admin Resource](gym_admin_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
