# PUT /api/v1/tracker/workouts/{tracker-workout-id}

Update a workout record in the tracker system.


---

## Permissions
| Permission                | Description                |
|---------------------------|----------------------------|
| `tracker_workouts.update` | Update tracker workout     |

---

## Request Body Parameters
| Name                    | Type    | Required | Description                                 |
|-------------------------|---------|----------|---------------------------------------------|
| `start`                 | string  | No       | Start datetime of the workout               |
| `workout_plan_session_id`| int    | No       | ID of the workout plan session (if based on a plan) |
| `workout_title`         | string  | No       | Optional title for the workout              |
| `end`                   | string  | No       | End datetime of the workout                 |
| `notes`                 | string  | No       | Optional notes                              |

*All parameters are optional. If omitted, they will not be updated. You can set them to null if desired.*

---

## Response

### 200 OK
```
<tracker workout resource>
```
- See [Tracker Workout Resource](tracker_workout_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 422    | Validation Error   | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
