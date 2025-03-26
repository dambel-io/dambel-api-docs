# `/api/v1/admin/brands/{brand-id}`
You can update an existing brand using this API.

- Method: `PUT`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions

- `brands.update`: to update a city

### Params

- `name`: Name of the brand (required|maxlength:255)
- `link`: A link to website of the brand (maxlength:255)
- `description`: An optional description for the brand

All of the parameters are optional. If you don't pass them, they won't get updated.
You still can set them to null if you want.

### Response

200:
```json
{
    "brand": {<brand resource>},
}
```

[Brand Resource](../../resources/brand.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
