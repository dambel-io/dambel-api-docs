# `/api/v1/admin/exercises`
This API creates a new exercise.

- Controller: [`App\Http\Controllers\API\V1\Admin\Exercises\CreateExerciseController`](../../../../src/app/Http/Controllers/API/V1/Admin/Exercises/CreateExerciseController.php)
- Method: `POST`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions

- `exercises.create`: to create an exercise

### Params

- `name`: Name of the exercise (required|maxlength:255)
- `link`: A link to a youtube video or something as a tutorial for the exercise (optional|maxlength:255)
- `description`: An optional description for the exercise

### Response

201:
```json
{
    "exercise": {<exercise resource>},
}
```

[Exercise Resource](../../resources/exercise.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
