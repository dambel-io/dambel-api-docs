# `/api/v1/admin/cities/{city-id}`
You can update an existing city using this API.

- Controller: [`App\Http\Controllers\API\V1\Admin\Cities\UpdateCityController`](../../../../src/app/Http/Controllers/API/V1/Admin/Cities/UpdateCityController.php)
- Method: `PUT`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions
- `cities.update`: to update a city

### Params

- `name`: Name of the city (required|maxlength:255)

### Response

200:
```json
{
    "city": {<city resource>},
}
```

[City Resource](../../resources/city.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
