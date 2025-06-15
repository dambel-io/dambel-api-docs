# `POST /api/v1/training/diet-plans`
You can create a diet plan using this API.


## Permissions

- `diet_plans.create`: creating diet plan for yourself or your trainee

## Params

- `title`: Title of the training service (maxlength 255)
- `description`: An optional description for the training service (maxlength 2000)
- `trainee_id`: Optional trainee id if you want to create the plan for one of your trainees

## Response

### 201 Created
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
