# `PUT /api/v1/gyms/{gym-id}/buffet-items/{buffet-item-id}`
You can update a buffet item using this API.


## Permissions

- `gym_buffet_items.update`: update your own gym buffet items
- `gym_buffet_items.update_any`: update buffet items for any gym

## Params

- `title`: Title of the item (maxlength 255)
- `description`: An optional description for the item (maxlength 2000)
- `price`: Price of the item (required integer)
- `discount`: Discount percentage (nullable float, default 0)

All of the parameters are optional. If you don't pass them, they won't get updated.
You still can set them to null if you want.

## Response

### 200 OK

```json
<gym buffet item resource>
```

[Training Service Resource](gym_buffet_item_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
