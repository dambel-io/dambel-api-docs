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
| `exercise_id`           | int     | Yes      | Exercise ID                                 |
| `is_replacement`        | boolean | No       | Whether this set is a replacement           |
| `rep_count`             | int     | Yes      | Number of repetitions                       |
| `weight`                | int     | No       | Weight used                                 |
| `end`                   | string  | No       | End datetime of the workout set             |
| `notes`                 | string  | No       | Optional notes                              |

---

## Response

### 201 Created
```
<tracker workout set resource>
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
