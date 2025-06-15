# `DELETE /api/v1/training/diet-plans/{diet-plan-id}`
You can delete a diet plan using this API.


## Permissions

- `diet_plans.delete`: deleting your own diet plans

## Response

### 204 No Content
Diet plan deleted.

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
