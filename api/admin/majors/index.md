# `/api/v1/admin/majors`
You can get list of the majors using this endpoint.

- Controller: [`App\Http\Controllers\API\V1\Admin\Majors\ListMajorController`](../../../../src/app/Http/Controllers/API/V1/Admin/Majors/ListMajorController.php)
- Method: `GET`

### Response

200:
```json
{
    "data": [
        {<major resource>},
        {<major resource>},
        {<major resource>},
        {<major resource>}
    ],
}
```

[Major Resource](../../resources/major.md)
