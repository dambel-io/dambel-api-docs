# `DELETE /api/v1/gyms/{gym-id}/admins/{admin-id}`
You can delete an admin from a gym using this API.


## Permissions

- `gym_admins.delete`: deleting admin from their own gyms
- `gym_admins.delete_any`: deleting admin of any gym

## Params

No parameter.

## Response

### 204 No Content
No content when admin gets deleted

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)
