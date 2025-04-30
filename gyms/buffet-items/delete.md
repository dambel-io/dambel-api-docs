# `DELETE /api/v1/gyms/{gym-id}/buffet-items/{buffet-item-id}`
You can delete a buffet item from a gym using this API.


## Permissions

- `gym_buffet_items.delete`: deleting your own gym buffet items
- `gym_buffet_items.delete_any`: deleting buffet items from any gym

## Params

No parameter.

## Response

### 204 No Content
No content when item gets deleted

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)
