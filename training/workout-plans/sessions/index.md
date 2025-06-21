# `GET /api/v1/training/workout-plans/{workout-plan-id}/sessions`
You can create a session for a workout plan using this API.


## Permissions

- `workout_plan_sessions.view`: to view sessions of your workout plans
- `workout_plans.view`: to be able to view your own workout plans

## Response

### 200 OK
```json
{
    "data": [<workout plan session resource>, ...],
}
```

[Workout Plan Session Resource](workout_plan_session_resource.md)

### 401 Unauthorized
[Authentication error](../../../_globals/authentication-errors.md)

### 404 Not Found
[Not-found error](../../../_globals/not-found-errors.md)

### 403 Forbidden
[Permission error](../../../_globals/permission-errors.md)
