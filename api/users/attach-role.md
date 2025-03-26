# `/api/v1/users/{user-id}/attach-role/{role-id}`
You can attach a role to a user using this API.

- Method: `POST`
- [Requires Authentication](../auth/login.md#how-to-use-api-token)

### Permissions
- `users.attach_role`: to attach role to any user except themselves

### Response

201:

```json
{
    "message": "Role attached successfully"
}
```

400:

```json
{
    "error": "User already has this role"
}
```

401: [Authentication error](../authentication-errors.md)

403: [Permission error](../permission-errors.md)

404: role or user not found ([Not-found error](../not-found-errors.md))
