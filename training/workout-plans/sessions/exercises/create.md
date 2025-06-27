# `POST /api/v1/training/workout-plans/{workout-plan-id}/sessions/{session-id}/exercises`
You can create a exercise for a workout plan using this API.


## Permissions

- `workout_plan_exercises.create`: to create exercises for your workout plans
- `workout_plans.update`: to be able to update your own workout plans

## Params

- `exercise_id`: Id of the exercise
- `super_set_id`: Id of the parent exercise if you want to define a super set
- `set_count`: Count of the sets
- `rep_count`: Count of the reps per each set
- `description`: An optional description for the exercise (maxlength 2000)

## Response

### 201 Created
```json
<workout plan exercise resource>
```

[Workout Plan Exercise Resource](workout_plan_exercise_resource.md)

### 422 Unprocessable Entity
[Validation error](../../../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../../../_globals/authentication-errors.md)

### 404 Not Found
[Not-found error](../../../../_globals/not-found-errors.md)

### 403 Forbidden
[Permission error](../../../../_globals/permission-errors.md)
