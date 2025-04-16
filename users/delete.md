# `DELETE /api/v1/users/{user-id}`
You can delete a user using this API.


## Permissions
- `users.delete_any`: to delete any user

## Response

### 204 No Content
 No content when user gets deleted

### 401 Unauthorized
[Authentication error](../authentication-errors.md)

### 403 Forbidden
[Permission error](../permission-errors.md)

### 404 Not Found
[Not-found error](../not-found-errors.md)
