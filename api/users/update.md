# `/api/v1/users/{user-id}`
Using this API you can update the information of one specific user.

- Controller: [`App\Http\Controllers\API\V1\Users\UpdateUserController`](../../../src/app/Http/Controllers/API/V1/Users/UpdateUserController.php)
- Method: `PUT`
- [Requires Authentication](../auth/login.md#how-to-use-api-token)

### Permissions
- `users.update_any`: to update any user as an admin

### Params

- `first_name`: First name of the user (required|maxlength:255)
- `last_name`: First name of the user (required|maxlength:255)
- `email`: Email of the user (required|maxlength:255|unique)
- `phone`: Phone number of the user (required|maxlength:255|unique)
- `password`: Optional parameter to set a new password for the user. Will be hashed and saved

All of the parameters are optional. If you don't pass them, they won't get updated.
You still can set them to null if you want. The required ones won't be able to be set to null

### Response

200:
```json
{
    "user": {<user resource>},
}
```

[User Resource](../resources/user.md)

404: wrong user id passed

422: [Validation error](../validation-errors.md)

401: [Authentication error](../authentication-errors.md)

403: [Permission error](../permission-errors.md)

409: newly set email/phone is already in use
