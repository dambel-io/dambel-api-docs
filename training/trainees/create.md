# `POST /api/v1/training/trainees`
You can create trainee records using this API.
Trainers can create trainees using this and also users can create a trainer from their side.


## Permissions

- `trainees.create`: creating trainees/trainers for yourself
- `trainees.create_any`: creating trainees/trainers for any user

## Params

- `user_id`: Id of the trainee user account
- `training_service_id`: Id of the training service
- `notes`: Optional notes

## Response

### 201 Created
```json
<trainee resource>
```

[Trainee Resource](trainee_resource.md)

### 400 Bad Request
When the account balance is not enough to pay for the training service.
The payment is not required if the creation is from trainer side.

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
