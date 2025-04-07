# `DELETE /api/v1/users/{user-id}/detach-role/{role-id}`
You can detach a role from a user using this API.


## Permissions
- `users.detach_role`: to attach role from any user except themselves

## Response

### 204 No Content


```json
{
    "message": "Role detached successfully"
}
```

### 400 Bad Request


```json
{
    "error": "User does not have this role"
}
```

### 401 Unauthorized
[Authentication error](../authentication-errors.md)

### 403 Forbidden
[Permission error](../permission-errors.md)

### 404 Not Found
 role or user not found ([Not-found error](../not-found-errors.md))
