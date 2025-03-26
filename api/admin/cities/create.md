# `/api/v1/admin/cities/{state}`
This API creates a new city.

- Controller: [`App\Http\Controllers\API\V1\Admin\Cities\CreateCityController`](../../../../src/app/Http/Controllers/API/V1/Admin/Cities/CreateCityController.php)
- Method: `POST`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions

- `cities.create`: to create a city

### Params

- `name`: Name of the city (required|maxlength:255)
- ID of the state in the route

### Response

201:
```json
{
    "city": {<city resource>},
}
```

[City Resource](../../resources/city.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
