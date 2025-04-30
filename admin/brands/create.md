# `POST /api/v1/admin/brands`
This API creates a new brand.


## Permissions

- `brands.create`: to create a brand

## Params

- `name`: Name of the brand (required|maxlength:255)
- `link`: A link to website of the brand (optional|maxlength:255)
- `description`: An optional description for the brand

## Response

### 201 Created
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
