# `PUT /api/v1/tracker/workouts/{tracker-workout-id}`
You can update a workout record in the tracker system using this API.


## Permissions

- `tracker_workouts.update`: updating tracker workout

## Params

- `start`: Start datetime of the workout
- `workout_plan_session_id`: Id of the workout plan session if it is based on a workout plan
- `workout_title`: An optional title for the workout
- `end`: End datetime of the workout
- `notes`: An optional notes

> Are parameters are optional. If you don't pass them, they remain as they are.

## Response

### 200 OK
```json
<tracker workout resource>
```

[Tracker Workout Resource](tracker_workout_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
