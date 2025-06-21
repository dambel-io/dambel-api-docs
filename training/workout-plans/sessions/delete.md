# `DELETE /api/v1/training/workout-plans/{workout-plan-id}/sessions/{session-id}`
You can delete a session from a workout plan using this API.


## Permissions

- `workout_plan_sessions.delete`: to delete sessions for your workout plans
- `workout_plans.update`: to be able to update your own workout plans

## Response

### 204 No Content
Session deleted.

### 401 Unauthorized
[Authentication error](../../../_globals/authentication-errors.md)

### 404 Not Found
[Not-found error](../../../_globals/not-found-errors.md)

### 403 Forbidden
[Permission error](../../../_globals/permission-errors.md)
