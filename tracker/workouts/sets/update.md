# `PUT /api/v1/tracker/workouts/{tracker-workout-id}/sets/{set-id}`
You can update a workout set record in the tracker system using this API.


## Permissions

- `tracker_workout_sets.update`: updating tracker workout

## Params

- `start`: Start datetime of the workout
- `workout_plan_exercise_id`: Id of the workout plan exercise if it is based on a workout plan
- `exercise_id`: Id of the exercise done
- `is_replacement`: A boolean to specify if this exercise is done instead of something else
- `rep_count`: Count of the reps
- `weight`: The weight used
- `end`: End datetime of the workout
- `notes`: An optional notes

> Are parameters are optional. If you don't pass them, they remain as they are.

## Response

### 200 OK
```json
<tracker workout set resource>
```

[Tracker Workout Set Resource](tracker_workout_set_resource.md)

### 422 Unprocessable Entity
[Validation error](../../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../../_globals/permission-errors.md)
