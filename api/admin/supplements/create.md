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
:
```json
{
    "supplement": {<supplement resource>},
}
```

[Supplement Resource](../../resources/supplement.md)

### 422 Unprocessable Entity
[Validation error](../../validation-errors.md)

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)
