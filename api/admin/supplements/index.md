# `/api/v1/admin/supplements`
You can get list of the supplements using this endpoint.

- Controller: [`App\Http\Controllers\API\V1\Admin\Supplements\ListSupplementController`](../../../../src/app/Http/Controllers/API/V1/Admin/Supplements/ListSupplementController.php)
- Method: `GET`

### Response

200:
```json
{
    "data": [
        {<supplement resource>},
        {<supplement resource>},
        {<supplement resource>},
        {<supplement resource>}
    ],
}
```

[Supplement Resource](../../resources/supplement.md)
