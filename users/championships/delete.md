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
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)
