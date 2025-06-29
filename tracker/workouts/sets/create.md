# `POST /api/v1/tracker/workouts/{workout-id}/sets`
You can record a workout set in the tracker system using this API.


## Permissions

- `tracker_workout_sets.create`: creating tracker workout set

## Params

- `start`: Start datetime of the workout
- `workout_plan_exercise_id`: Id of the workout plan exercise if it is based on a workout plan
- `exercise_id`: Id of the exercise done
- `is_replacement`: A boolean to specify if this exercise is done instead of something else
- `rep_count`: Count of the reps
- `weight`: The weight used
- `end`: End datetime of the workout
- `notes`: An optional notes

## Response

### 201 Created
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
