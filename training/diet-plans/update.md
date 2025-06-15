# `PUT /api/v1/training/diet-plans/{diet-plan-id}`
You can update a diet plan using this API.


## Permissions

- `diet_plans.update`: updating your own or trainee's diet plans

## Params

- `title`: Title of the training service (maxlength 255)
- `description`: An optional description for the training service (maxlength 2000)

## Response

### 200 OK
```json
<diet plan resource>
```

[Diet Plan Resource](diet_plan_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
