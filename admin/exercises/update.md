# `PUT /api/v1/admin/exercises/{exercise-id}`
You can update an existing exercise using this API.


## Permissions

- `exercises.update`: to update a exercise

## Params

- `name`: Name of the exercise (required|maxlength:255)
- `link`: A link to a youtube video or something as a tutorial for the exercise (maxlength:255)
- `description`: An optional description for the exercise

All of the parameters are optional. If you don't pass them, they won't get updated.
You still can set them to null if you want.

## Response

### 200 OK

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
