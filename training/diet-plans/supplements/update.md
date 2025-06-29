# `PUT /api/v1/training/diet-plans/{diet-plan-id}/supplements/{supplement-id}`
You can update a supplement from a diet plan using this API.


## Permissions

- `diet_plan_supplements.update`: to update supplements for your diet plans
- `diet_plans.update`: to be able to update your own diet plans

## Params

- `supplement_id`: Id of the supplement
- `amount`: How much to consume (integer)
- `amount_unit`: A string to define the unit (.e.g. `mg`, `g`, etc.)
- `description`: An optional description for the training service (maxlength 2000)
- `after_meal_index`: Index of the meal to define after/with/before which meal should this be consumed

## Response

### 200 OK
```json
<diet plan supplement resource>
```

[Diet Plan Supplement Resource](diet_plan_supplement_resource.md)

### 422 Unprocessable Entity
[Validation error](../../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../../_globals/authentication-errors.md)

### 404 Not Found
[Not-found error](../../../_globals/not-found-errors.md)

### 403 Forbidden
[Permission error](../../../_globals/permission-errors.md)
