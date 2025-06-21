# `PUT /api/v1/training/workout-plans/{workout-plan-id}/sessions/{session-id}`
You can update a session from a workout plan using this API.


## Permissions

- `workout_plan_sessions.update`: to update sessions for your workout plans
- `workout_plans.update`: to be able to update your own workout plans

## Params

- `title`: Title of the session (maxlength 255, e.g. `Leg Day`)
- `day`: Weekday of the session (`saturday`, `monday`, etc.)
- `description`: An optional description for the session (maxlength 2000)

## Response

### 200 OK
```json
<workout plan session resource>
```

[Workout Plan Session Resource](workout_plan_session_resource.md)

### 422 Unprocessable Entity
[Validation error](../../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../../_globals/authentication-errors.md)

### 404 Not Found
[Not-found error](../../../_globals/not-found-errors.md)

### 403 Forbidden
[Permission error](../../../_globals/permission-errors.md)
