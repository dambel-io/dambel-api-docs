# `DELETE /api/v1/training/diet-plans/{diet-plan-id}/supplements/{supplement-id}`
You can delete a supplement from a diet plan using this API.


## Permissions

- `diet_plan_supplements.delete`: to delete supplements for your diet plans
- `diet_plans.update`: to be able to update your own diet plans

## Response

### 204 No Content
Supplement deleted.

### 401 Unauthorized
[Authentication error](../../../_globals/authentication-errors.md)

### 404 Not Found
[Not-found error](../../../_globals/not-found-errors.md)

### 403 Forbidden
[Permission error](../../../_globals/permission-errors.md)
