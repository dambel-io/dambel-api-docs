# `DELETE /api/v1/training/services/{training-service-id}`
You can delete a training service from a user using this API.


## Permissions

- `training_services.delete`: deleting your own training services
- `training_services.delete_any`: deleting training services from any user

## Params

No parameter.

## Response

### 204 No Content
No content when training service gets deleted

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)
