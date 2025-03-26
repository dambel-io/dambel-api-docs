# `/api/v1/users/{user-id}`
You can delete a user using this API.

- Controller: [`App\Http\Controllers\API\V1\Users\DeleteUserController`](../../../src/app/Http/Controllers/API/V1/Users/DeleteUserController.php)
- Method: `DELETE`
- [Requires Authentication](../auth/login.md#how-to-use-api-token)

### Permissions
- `users.delete_any`: to delete any user

### Response

204: No content when user gets deleted

401: [Authentication error](../authentication-errors.md)

403: [Permission error](../permission-errors.md)

404: [Not-found error](../not-found-errors.md)
