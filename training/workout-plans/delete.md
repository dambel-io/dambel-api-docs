# `DELETE /api/v1/training/workout-plans/{workout-plan-id}`
You can delete a workout plan using this API.


## Permissions

- `workout_plans.delete`: deleting your own workout plans

## Response

### 204 No Content
Workout plan deleted.

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
