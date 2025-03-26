# `/api/v1/admin/brands`
This API creates a new brand.

- Controller: [`App\Http\Controllers\API\V1\Admin\Brands\CreateBrandController`](../../../../src/app/Http/Controllers/API/V1/Admin/Brands/CreateBrandController.php)
- Method: `POST`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions

- `brands.create`: to create a brand

### Params

- `name`: Name of the brand (required|maxlength:255)
- `link`: A link to website of the brand (optional|maxlength:255)
- `description`: An optional description for the brand

### Response

201:
```json
{
    "brand": {<brand resource>},
}
```

[Brand Resource](../../resources/brand.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
