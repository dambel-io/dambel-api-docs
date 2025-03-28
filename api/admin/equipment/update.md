# `PUT /api/v1/admin/equipment/{equipment-id}`
You can update an existing equipment using this API.


### Permissions

- `equipment.update`: to update an equipment

### Params

- `name`: Name of the equipment (required|maxlength:255)
- `link`: A link to a youtube video or something as a tutorial for the equipment (maxlength:255)
- `description`: An optional description for the equipment

All of the parameters are optional. If you don't pass them, they won't get updated.
You still can set them to null if you want.

### Response

200:
```json
{
    "equipment": {<equipment resource>},
}
```

[Exercise Resource](../../resources/equipment.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
