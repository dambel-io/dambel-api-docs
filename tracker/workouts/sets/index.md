# `GET /api/v1/tracker/workouts/{tracker-workout-id}/sets`
You can get a list of workout set records in the tracker system.


## Permissions

- `tracker_workout_sets.view`: viewing tracker workout set

## Response

### 200 OK

```json
{
    "data": [
        {<tracker workout set resource>},
        {<tracker workout set resource>}
    ],
    "links": {<pagination data>},
    "meta": {<pagination data>},
}
```

[Tracker Workout Set Resource](tracker_workout_set_resource.md)

### 401 Unauthorized
[Authentication error](../../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../../_globals/permission-errors.md)
