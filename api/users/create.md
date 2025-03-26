# `/api/v1/users`
This API creates a new user.

- Controller: [`App\Http\Controllers\API\V1\Users\CreateUserController`](../../../src/app/Http/Controllers/API/V1/Users/CreateUserController.php)
- Method: `POST`
- [Requires Authentication](../auth/login.md#how-to-use-api-token)

### Permissions
- `users.create`: to create users

### Params

- `first_name`: First name of the user (required|maxlength:255)
- `last_name`: First name of the user (required|maxlength:255)
- `email`: Email of the user (required|maxlength:255|unique)
- `phone`: Phone number of the user (required|maxlength:255|unique)
- `password`: Required parameter to set password of the user. Will be hashed and saved

### Response

201:
```json
{
    "user": {<user resource>},
}
```

[User Resource](../resources/user.md)

422: [Validation error](../validation-errors.md)

409: Email/Phone already in use

401: [Authentication error](../authentication-errors.md)

403: [Permission error](../permission-errors.md)
