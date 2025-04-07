# `POST /api/v1/admin/equipment`
This API creates a new equipment.


## Permissions

- `equipment.create`: to create an equipment

## Params

- `name`: Name of the equipment (required|maxlength:255)
- `link`: A link to a youtube video or something as a tutorial for the equipment (optional|maxlength:255)
- `description`: An optional description for the equipment

## Response

### 201 Created
:
```json
{
    "equipment": {<equipment resource>},
}
```

[Equipment Resource](../../resources/equipment.md)

### 422 Unprocessable Entity
[Validation error](../../validation-errors.md)

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)
