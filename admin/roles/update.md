# `PUT /api/v1/admin/roles/{role-id}`
You can update an existing role using this API.


## Permissions
- `roles.update`: to update a role

## Params

- `name`: Name of the role (required|maxlength:255)
- `permissions`: An array containing list of the permissions (optional)

## Response

### 200 OK

```json
<role resource>
```

[Role Resource](role.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not found error](../../_globals/not-found-errors.md)
