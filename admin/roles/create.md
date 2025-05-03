# `POST /api/v1/admin/roles`
This API creates a new state.


## Permissions

- `roles.view_all`: to access roles
- `roles.create`: to create a role

## Params

- `name`: Name of the role (required|maxlength:255)
- `permissions`: An array containing list of the permissions (optional)

## Response

### 201 Created
```json
<role resource>
```

[Role Resource](role_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
