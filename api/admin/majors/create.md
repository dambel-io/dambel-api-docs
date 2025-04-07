# `POST /api/v1/admin/majors`
This API creates a new major.


## Permissions
- `majors.create`: to create a country

## Params

- `title`: Name of the major (required|maxlength:255)

## Response

### 201 Created
:
```json
{
    "major": {<major resource>},
}
```

[Major Resource](../../resources/major.md)

### 422 Unprocessable Entity
[Validation error](../../validation-errors.md)

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)
