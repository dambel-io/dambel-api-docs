# PUT /api/v1/tracker/workouts/{tracker-workout-id}/sets/{set-id}

Update a workout set record in the tracker system.


---

## Permissions
| Permission                      | Description                |
|----------------------------------|----------------------------|
| `tracker_workout_sets.update`    | Update tracker workout set |

---

## Request Body Parameters
| Name                    | Type    | Required | Description                                 |
|-------------------------|---------|----------|---------------------------------------------|
| `start`                 | string  | No       | Start datetime of the workout set           |
| `workout_plan_exercise_id`| int   | No       | Workout plan exercise ID (if applicable)    |
| `exercise_id`           | int     | No       | Catalog exercise ID. Setting it clears `custom_name` |
| `custom_name`           | string  | No       | Free-text movement name (max 255, trimmed). Setting it clears `exercise_id` |
| `is_replacement`        | boolean | No       | Whether this set is a replacement           |
| `rep_count`             | int     | No       | Number of repetitions                       |
| `weight`                | int     | No       | Weight used                                 |
| `end`                   | string  | No       | End datetime of the workout set             |
| `notes`                 | string  | No       | Optional notes                              |

*All parameters are optional. If omitted, they will not be updated. You can set them to null if desired.*

When a request sends `exercise_id` or `custom_name`, the set must end up with exactly one of them: sending
both is a 422 naming both fields, and clearing the only one it has (`{"exercise_id": null}` on a catalog set)
is a 422 on `custom_name`. A request that touches neither field is not checked, so a set logged before custom
names existed can still be edited.

---

## Response

### 200 OK
```json
{
  "data": { /* tracker workout set resource */ }
}
```
- See [Tracker Workout Set Resource](tracker_workout_set_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 422    | Validation Error   | [Validation error](../../../_globals/validation-errors.md)         |
| 401    | Unauthorized       | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../../_globals/permission-errors.md)         |

---
