# `POST /api/v1/admin/majors`
This API creates a new major.


## Permissions

- `majors.view_all`: to access majors
- `majors.create`: to create a country

## Params

- `title`: Name of the major (required|maxlength:255)

## Response

### 201 Created
```json
{
    "major": {<major resource>},
}
```

[Major Resource](major_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
