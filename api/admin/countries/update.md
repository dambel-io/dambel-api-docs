# `/api/v1/admin/countries/{country-id}`
You can update an existing country using this API.

- Controller: [`App\Http\Controllers\API\V1\Admin\Countries\UpdateCountryController`](../../../../src/app/Http/Controllers/API/V1/Admin/Countries/UpdateCountryController.php)
- Method: `PUT`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions
- `countries.update`: to update a country

### Params

- `name`: Name of the country (required|maxlength:255)

### Response

200:
```json
{
    "country": {<country resource>},
}
```

[Country Resource](../../resources/country.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
