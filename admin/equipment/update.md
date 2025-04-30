# `PUT /api/v1/admin/equipment/{equipment-id}`
You can update an existing equipment using this API.


## Permissions

- `equipment.update`: to update an equipment

## Params

- `name`: Name of the equipment (required|maxlength:255)
- `link`: A link to a youtube video or something as a tutorial for the equipment (maxlength:255)
- `description`: An optional description for the equipment

All of the parameters are optional. If you don't pass them, they won't get updated.
You still can set them to null if you want.

## Response

### 200 OK

```json
{
    "equipment": {<equipment resource>},
}
```

[Exercise Resource](equipment_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
