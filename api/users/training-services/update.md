# `PUT /api/v1/users/{user-id}/training-services/{training-service-id}`
You can update a training service using this API.


## Permissions

- `training_services.update`: update your own training services
- `training_services.update_any`: update training services for any user

## Params

- `title`: Title of the training service (maxlength 255)
- `description`: An optional description for the training service (maxlength 2000)
- `price`: Price of the training service (required integer)

All of the parameters are optional. If you don't pass them, they won't get updated.
You still can set them to null if you want.

## Response

### 200 OK

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
