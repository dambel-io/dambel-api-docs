# `/api/v1/admin/countries`
You can get list of the countries by alphabetical order using this endpoint.

- Controller: [`App\Http\Controllers\API\V1\Admin\Countries\ListCountryController`](../../../../src/app/Http/Controllers/API/V1/Admin/Countries/ListCountryController.php)
- Method: `GET`

### Response

200:
```json
{
    "data": [
        {<country resource>},
        {<country resource>},
        {<country resource>},
        {<country resource>}
    ],
}
```

[Country Resource](../../resources/country.md)
