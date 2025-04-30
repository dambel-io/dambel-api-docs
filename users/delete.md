# `DELETE /api/v1/users/{user-id}`
You can delete a user using this API.


## Permissions
- `users.delete_any`: to delete any user

## Response

### 204 No Content
 No content when user gets deleted

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../_globals/not-found-errors.md)
