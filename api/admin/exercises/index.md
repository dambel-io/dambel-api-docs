# `/api/v1/admin/exercises`
You can get list of the exercises by alphabetical order using this endpoint.

- Controller: [`App\Http\Controllers\API\V1\Admin\Exercises\ListExerciseController`](../../../../src/app/Http/Controllers/API/V1/Admin/Exercises/ListExerciseController.php)
- Method: `GET`

### Response

200:
```json
{
    "data": [
        {<exercise resource>},
        {<exercise resource>},
        {<exercise resource>},
        {<exercise resource>}
    ],
}
```

[Exercise Resource](../../resources/exercise.md)
