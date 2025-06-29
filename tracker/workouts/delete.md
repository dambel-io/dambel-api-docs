# `DELETE /api/v1/tracker/workouts/{tracker-workout-id}`
You can delete a workout record in the tracker system using this API.


## Permissions

- `tracker_workouts.delete`: deleting tracker workout

## Response

### 204 No Content
Record deleted.

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
