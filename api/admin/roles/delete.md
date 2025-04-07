# `DELETE /api/v1/admin/roles/{role-id}`
You can delete a role using this endpoint.


## Permissions
- `roles.delete`: to delete any role

## Response

### 204 No Content
 No content when state gets deleted

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)

### 404 Not Found
[Not-found error](../../not-found-errors.md)
