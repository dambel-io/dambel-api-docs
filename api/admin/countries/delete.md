# `/api/v1/admin/countries/{country-id}`
You can delete a country using this endpoint.

- Controller: [`App\Http\Controllers\API\V1\Admin\Countries\DeleteCountryController`](../../../../src/app/Http/Controllers/API/V1/Admin/Countries/DeleteCountryController.php)
- Method: `DELETE`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions
- `countries.delete`: to delete any country

### Params

- `replacement_id`: In case the country you are deleting has some data attached to it, you transfer the data to another country by providing it's ID in this optional parameter

### Response

204: No content when country gets deleted

400: When country has data and `replacement_id` is not provided or is not valid. Number of attached items are returned in `attached_data`.

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)

404: [Not-found error](../../not-found-errors.md)
