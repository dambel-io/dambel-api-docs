# `/api/v1/admin/roles`
This API creates a new state.

- Controller: [`App\Http\Controllers\API\V1\Admin\Roles\CreateRoleController`](../../../../src/app/Http/Controllers/API/V1/Admin/Roles/CreateRoleController.php)
- Method: `POST`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions

- `roles.create`: to create a role

### Params

- `name`: Name of the role (required|maxlength:255)
- `permissions`: An array containing list of the permissions (optional)

### Response

201:
```json
<role resource>
```

[Role Resource](../../resources/role.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
