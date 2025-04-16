# `POST /api/v1/admin/exercises`
This API creates a new exercise.


## Permissions

- `exercises.create`: to create an exercise

## Params

- `name`: Name of the exercise (required|maxlength:255)
- `link`: A link to a youtube video or something as a tutorial for the exercise (optional|maxlength:255)
- `description`: An optional description for the exercise

## Response

### 201 Created
:
```json
{
    "exercise": {<exercise resource>},
}
```

[Exercise Resource](../../resources/exercise.md)

### 422 Unprocessable Entity
[Validation error](../../validation-errors.md)

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)
