# `/api/v1/admin/majors/{major-id}`
You can update an existing major using this API.

- Controller: [`App\Http\Controllers\API\V1\Admin\Majors\UpdateMajorController`](../../../../src/app/Http/Controllers/API/V1/Admin/Majors/UpdateMajorController.php)
- Method: `PUT`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions
- `majors.update`: to update a major

### Params

- `title`: Title of the major (required|maxlength:255)

### Response

200:
```json
{
    "major": {<major resource>},
}
```

[Major Resource](../../resources/major.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
