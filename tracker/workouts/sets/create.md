# POST /api/v1/tracker/workouts/{workout-id}/sets

Record a new workout set in the tracker system.


---

## Permissions
| Permission                      | Description                |
|----------------------------------|----------------------------|
| `tracker_workout_sets.create`    | Create tracker workout set |

---

## Request Body Parameters
| Name                    | Type    | Required | Description                                 |
|-------------------------|---------|----------|---------------------------------------------|
| `start`                 | string  | Yes      | Start datetime of the workout set           |
| `workout_plan_exercise_id`| int   | No       | Workout plan exercise ID (if applicable)    |
| `exercise_id`           | int     | One of   | Catalog exercise ID. Required unless `custom_name` is sent; must not be sent with it |
| `custom_name`           | string  | One of   | Free-text movement name (max 255, trimmed). Required unless `exercise_id` is sent; must not be sent with it |
| `is_replacement`        | boolean | No       | Whether this set is a replacement           |
| `rep_count`             | int     | Yes      | Number of repetitions                       |
| `weight`                | int     | No       | Weight used                                 |
| `end`                   | string  | No       | End datetime of the workout set             |
| `notes`                 | string  | No       | Optional notes                              |

Send **exactly one** of `exercise_id` or `custom_name`; both or neither is a 422 naming both fields, and a
whitespace-only `custom_name` counts as not sent. To log a set of a **custom plan exercise**, send that plan
exercise's `custom_name` together with its `workout_plan_exercise_id`. A custom set is never an exercise
[record](../../data/records.md), never appears in previous-sets history, cannot be claimed as a
[strength record](../../strength-records/create.md), and credits no muscle group in the tracker muscle load.

---

## Response

### 201 Created
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
