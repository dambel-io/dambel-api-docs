# `POST /api/v1/users/{user-id}/training-services`
You can create a training service for a user using this API.


## Permissions

- `training_services.create`: creating training services for yourself
- `training_services.create_any`: creating training services for any user

## Params

- `title`: Title of the training service (maxlength 255)
- `description`: An optional description for the training service (maxlength 2000)
- `price`: Price of the training service (required integer)

## Response

### 201 Created
:
```json
<training service resource>
```

[Training Service Resource](../../resources/training_service.md)

### 422 Unprocessable Entity
[Validation error](../../validation-errors.md)

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)
