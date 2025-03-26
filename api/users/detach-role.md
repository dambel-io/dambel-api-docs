# `/api/v1/users/{user-id}/detach-role/{role-id}`
You can detach a role from a user using this API.

- Controller: [`App\Http\Controllers\API\V1\Users\DetachRoleFromUserController`](../../../src/app/Http/Controllers/API/V1/Users/DetachRoleFromUserController.php)
- Method: `DELETE`
- [Requires Authentication](../auth/login.md#how-to-use-api-token)

### Permissions
- `users.detach_role`: to attach role from any user except themselves

### Response

204:

```json
{
    "message": "Role detached successfully"
}
```

400:

```json
{
    "error": "User does not have this role"
}
```

401: [Authentication error](../authentication-errors.md)

403: [Permission error](../permission-errors.md)

404: role or user not found ([Not-found error](../not-found-errors.md))
