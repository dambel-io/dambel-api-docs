# `POST /api/v1/gyms/{gym-id}/admins`
You can create an admin for a gym using this API.


## Permissions

- `gym_admins.create`: creating admins for your own gyms
- `gym_admins.create_any`: creating admins for any gym

## Params

- `title`: Title of the admin (optional, maxlength 255)
- `user_id`: Id of the user that you want to give access to
- `permissions`: List of the permission names as an array

## Response

### 201 Created
```json
<gym admin resource>
```

[Gym admin Resource](gym_admin_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
