# `POST /api/v1/training/workout-plans`
You can create a workout plan using this API.


## Permissions

- `workout_plans.create`: creating workout plan for yourself or your trainee

## Params

- `title`: Title of the workout plan (maxlength 255)
- `description`: An optional description for the workout plan (maxlength 2000)
- `trainee_id`: Optional trainee id if you want to create the plan for one of your trainees

## Response

### 201 Created
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
