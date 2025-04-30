# `PUT /api/v1/admin/brands/{brand-id}`
You can update an existing brand using this API.


## Permissions

- `brands.update`: to update a city

## Params

- `name`: Name of the brand (required|maxlength:255)
- `link`: A link to website of the brand (maxlength:255)
- `description`: An optional description for the brand

All of the parameters are optional. If you don't pass them, they won't get updated.
You still can set them to null if you want.

## Response

### 200 OK

```json
{
    "brand": {<brand resource>},
}
```

[Brand Resource](brand_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
