# `DELETE /api/v1/training/workout-plans/{workout-plan-id}/sessions/{session-id}/exercises/{exercise-id}`
You can delete a exercise from a workout plan using this API.


## Permissions

- `workout_plan_exercises.delete`: to delete exercises for your workout plans
- `workout_plans.update`: to be able to update your own workout plans

## Response

### 204 No Content
Exercise deleted.

### 401 Unauthorized
[Authentication error](../../../../_globals/authentication-errors.md)

### 404 Not Found
[Not-found error](../../../../_globals/not-found-errors.md)

### 403 Forbidden
[Permission error](../../../../_globals/permission-errors.md)
