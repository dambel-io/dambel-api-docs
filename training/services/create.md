# `POST /api/v1/training/services/{user-id}`
You can create a training service for a user using this API.


## Permissions

- `training_services.create`: creating training services for yourself
- `training_services.create_any`: creating training services for any user

## Params

- `title`: Title of the training service (maxlength 255)
- `description`: An optional description for the training service (maxlength 2000)
- `price`: Price of the training service (required integer)
- `discount`: Discount percentage (nullable float, default 0)
- Id of the user in the route

## Response

### 201 Created
```json
<training service resource>
```

[Training Service Resource](training_service_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
