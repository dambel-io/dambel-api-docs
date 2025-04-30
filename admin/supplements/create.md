# `POST /api/v1/admin/supplements`
This API creates a new supplement.


## Permissions

- `supplements.create`: to create a supplement

## Params

- `title`: Name of the supplement (required|maxlength:255)
- `link`: A link to a wiki page for the supplement (optional|maxlength:255)
- `description`: An optional description for the supplement

## Response

### 201 Created
```json
{
    "supplement": {<supplement resource>},
}
```

[Supplement Resource](supplement_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
