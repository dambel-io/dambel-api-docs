# `POST /api/v1/users/{user-id}/attach-role/{role-id}`
You can attach a role to a user using this API.


## Permissions
- `users.attach_role`: to attach role to any user except themselves

## Response

### 201 Created
:

```json
{
    "message": "Role attached successfully"
}
```

### 400 Bad Request


```json
{
    "error": "User already has this role"
}
```

### 401 Unauthorized
 [Authentication error](../authentication-errors.md)

### 403 Forbidden
 [Permission error](../permission-errors.md)

### 404 Not Found
 role or user not found ([Not-found error](../not-found-errors.md))
