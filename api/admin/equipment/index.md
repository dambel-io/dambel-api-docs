# `/api/v1/admin/equipment`
You can get list of the equipment by alphabetical order using this endpoint.

- Controller: [`App\Http\Controllers\API\V1\Admin\Equipment\ListEquipmentController`](../../../../src/app/Http/Controllers/API/V1/Admin/Equipment/ListEquipmentController.php)
- Method: `GET`

### Response

200:
```json
{
    "data": [
        {<equipment resource>},
        {<equipment resource>},
        {<equipment resource>},
        {<equipment resource>}
    ],
}
```

[Equipment Resource](../../resources/equipment.md)
