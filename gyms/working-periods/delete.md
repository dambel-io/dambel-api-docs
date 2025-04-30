# `DELETE /api/v1/gyms/{gym-id}/working-periods/{working-period-id}`
You can delete a working period from a gym using this API.


## Permissions

- `gym_working_periods.delete`: deleting working periods from their own gyms
- `gym_working_periods.delete_any`: deleting working period of any gym

## Params

No parameter.

## Response

### 204 No Content
 No content when working period gets deleted

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)
