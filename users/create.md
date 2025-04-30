# `POST /api/v1/users`
This API creates a new user.


## Permissions
- `users.create`: to create users

## Params

- `first_name`: First name of the user (required|maxlength:255)
- `last_name`: First name of the user (required|maxlength:255)
- `email`: Email of the user (required|maxlength:255|unique)
- `phone`: Phone number of the user (required|maxlength:255|unique)
- `password`: Required parameter to set password of the user. Will be hashed and saved

## Response

### 201 Created
```json
{
    "user": {<user resource>},
}
```

[User Resource](user_resource.md)

### 422 Unprocessable Entity
[Validation error](../_globals/validation-errors.md)

409: Email/Phone already in use

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)
