# `DELETE /api/v1/gyms/{gym-id}/plans/{plan-id}`
You can delete a subscription plan from a gym using this API.


## Permissions

- `gym_plans.delete`: deleting gym plan from their own gyms
- `gym_plans.delete_any`: deleting gym plan of any gym

## Params

No parameter.

## Response

### 204 No Content
 No content when plan gets deleted

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)
