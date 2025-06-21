# `PUT /api/v1/training/workout-plans/{workout-plan-id}`
You can update a workout plan using this API.


## Permissions

- `workout_plans.update`: updating your own or trainee's workout plans

## Params

- `title`: Title of the workout plan (maxlength 255)
- `description`: An optional description for the workout plan (maxlength 2000)

## Response

### 200 OK
```json
<workout plan resource>
```

[Workout Plan Resource](workout_plan_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
