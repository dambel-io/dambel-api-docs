# `POST /api/v1/gyms/{gym-id}/buffet-items`
You can create a buffet item for a gym using this API.


## Permissions

- `buffet_items.create`: creating buffet items for your own gym
- `buffet_items.create_any`: creating buffet items for any gym

## Params

- `title`: Title of the item (maxlength 255)
- `description`: An optional description for the item (maxlength 2000)
- `price`: Price of the item (required integer)

## Response

### 201 Created
:
```json
<gym buffet item resource>
```

[Gym Buffet Item Resource](../../resources/gym_buffet_item.md)

### 422 Unprocessable Entity
[Validation error](../../validation-errors.md)

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)
