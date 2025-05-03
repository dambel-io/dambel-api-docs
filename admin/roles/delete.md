# `DELETE /api/v1/admin/roles/{role-id}`
You can delete a role using this endpoint.


## Permissions

- `roles.view_all`: to access roles
- `roles.delete`: to delete any role

## Response

### 204 No Content
 No content when state gets deleted

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)
