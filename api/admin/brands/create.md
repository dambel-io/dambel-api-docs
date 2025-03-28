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
:
```json
{
    "brand": {<brand resource>},
}
```

[Brand Resource](../../resources/brand.md)

### 422 Unprocessable Entity
 [Validation error](../../validation-errors.md)

### 401 Unauthorized
 [Authentication error](../../authentication-errors.md)

### 403 Forbidden
 [Permission error](../../permission-errors.md)
