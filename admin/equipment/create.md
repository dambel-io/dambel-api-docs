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
```json
{
    "equipment": {<equipment resource>},
}
```

[Equipment Resource](equipment_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
