# `PUT /api/v1/gyms/{gym-id}/buffet-items/{buffet-item-id}`
You can update a buffet item using this API.


## Permissions

- `gym_buffet_items.update`: update your own gym buffet items
- `gym_buffet_items.update_any`: update buffet items for any gym

## Params

- `title`: Title of the item (maxlength 255)
- `description`: An optional description for the item (maxlength 2000)
- `price`: Price of the item (required integer)

All of the parameters are optional. If you don't pass them, they won't get updated.
You still can set them to null if you want.

## Response

### 200 OK

```json
<gym buffet item resource>
```

[Training Service Resource](../../resources/gym_buffet_item.md)

### 422 Unprocessable Entity
[Validation error](../../validation-errors.md)

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)
