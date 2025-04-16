# `DELETE /api/v1/users/{user-id}/championships/{championship-id}`
You can delete a championship from a user using this API.


## Permissions

- `championships.delete`: deleting your own championships
- `championships.delete_any`: deleting championship from any user

## Params

No parameter.

## Response

### 204 No Content
 No content when championship gets deleted

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)

### 404 Not Found
[Not-found error](../../not-found-errors.md)
