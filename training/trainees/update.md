# `PUT /api/v1/training/trainees/{trainee-id}`
You can update a trainee using this API.


## Permissions

- `trainees.update`: update your own trainees/trainers
- `trainees.update_any`: update trainees/trainers for any user

## Params

- `notes`: Optional notes
- `is_delivered`: Optional boolean to specify if the service is delivered (Only trainer can update this field)

All of the parameters are optional. If you don't pass them, they won't get updated.
You still can set them to null if you want.

## Response

### 200 OK

```json
<trainee resource>
```

[Trainee Resource](trainee_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
