# `/api/v1/admin/roles/{role-id}`
You can update an existing role using this API.

- Method: `PUT`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions
- `roles.update`: to update a role

### Params

- `name`: Name of the role (required|maxlength:255)
- `permissions`: An array containing list of the permissions (optional)

### Response

200:
```json
<role resource>
```

[Role Resource](../../resources/role.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)

404: [Not found error](../../not-found-errors.md)
