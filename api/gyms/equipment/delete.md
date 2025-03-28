# `DELETE /api/v1/gyms/{gym-id}/equipment/{gym-equipment-id}`
You can delete an equipment from a gym using this API.


## Permissions

- `gym_equipment.delete`: deleting equipment from their own gyms
- `gym_equipment.delete_any`: deleting equipment of any gym

## Params

No parameter.

## Response

### 204 No Content
 No content when equipment gets deleted

### 401 Unauthorized
 [Authentication error](../../authentication-errors.md)

### 403 Forbidden
 [Permission error](../../permission-errors.md)

### 404 Not Found
 [Not-found error](../../not-found-errors.md)
