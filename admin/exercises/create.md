# `POST /api/v1/admin/exercises`
This API creates a new exercise.


## Permissions

- `exercises.view_all`: to access exercises
- `exercises.create`: to create an exercise

## Params

- `name`: Name of the exercise (required|maxlength:255)
- `link`: A link to a youtube video or something as a tutorial for the exercise (optional|maxlength:255)
- `description`: An optional description for the exercise

## Response

### 201 Created
```json
{
    "exercise": {<exercise resource>},
}
```

[Exercise Resource](exercise_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
