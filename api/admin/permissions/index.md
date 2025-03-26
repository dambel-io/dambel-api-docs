# `/api/v1/admin/permissions`
You can get list of the permissions using this API.

- Controller: [`App\Http\Controllers\API\V1\Admin\Permissions\ListPermissionController`](../../../../src/app/Http/Controllers/API/V1/Admin/Permissions/ListPermissionController.php)
- Method: `GET`

### Response

200:
```json
{
    "data": [
        {<permission resource>},
        {<permission resource>},
        {<permission resource>},
        {<permission resource>}
    ],
}
```

[Permission Resource](../../resources/permission.md)
