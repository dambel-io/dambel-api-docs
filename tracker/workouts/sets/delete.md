# `DELETE /api/v1/tracker/workouts/{tracker-workout-id}/sets/{workout-set-id}`
You can delete a workout set record in the tracker system using this API.


## Permissions

- `tracker_workout_sets.delete`: deleting tracker workout set

## Response

### 204 No Content
Record deleted.

### 401 Unauthorized
[Authentication error](../../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../../_globals/permission-errors.md)
