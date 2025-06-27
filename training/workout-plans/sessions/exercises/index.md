# `GET /api/v1/training/workout-plans/{workout-plan-id}/sessions/{session-id}/exercises`
You can create a exercise for a workout plan using this API.


## Permissions

- `workout_plan_exercises.view`: to view exercises of your workout plans
- `workout_plans.view`: to be able to view your own workout plans

## Response

### 200 OK
```json
{
    "data": [<workout plan exercise resource>, ...],
}
```

[Workout Plan Exercise Resource](workout_plan_exercise_resource.md)

### 401 Unauthorized
[Authentication error](../../../../_globals/authentication-errors.md)

### 404 Not Found
[Not-found error](../../../../_globals/not-found-errors.md)

### 403 Forbidden
[Permission error](../../../../_globals/permission-errors.md)
