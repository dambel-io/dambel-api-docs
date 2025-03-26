# `/api/v1/admin/brands`
You can get list of the brands by alphabetical order using this endpoint.

- Controller: [`App\Http\Controllers\API\V1\Admin\Brands\ListBrandController`](../../../../src/app/Http/Controllers/API/V1/Admin/Brands/ListBrandController.php)
- Method: `GET`

### Response

200:
```json
{
    "data": [
        {<brand resource>},
        {<brand resource>},
        {<brand resource>},
        {<brand resource>}
    ],
}
```

[Brand Resource](../../resources/brand.md)
