# Workout Plan Exercise Resource

Represents an exercise in a workout plan session.


---

## Schema
| Field                   | Type    | Description                                 |
|-------------------------|---------|---------------------------------------------|
| `id`                    | integer | Exercise ID                                 |
| `workout_plan_session_id`| integer| Associated session ID                       |
| `exercise_id`           | integer | Exercise ID                                 |
| `exercise`           | [Exercise Resource](../../../../admin/exercises/exercise_resource.md) | Exercise data                                 |
| `super_set_id`          | integer | Parent exercise ID for supersets (nullable) |
| `set_count`             | int     | Number of sets                              |
| `rep_count`             | int     | Number of reps per set                      |
| `description`           | string  | Description                                 |

---

## Example
```json
{
  "id": 123,
  "workout_plan_session_id": 123,
  "exercise_id": 123,
  "super_set_id": null,
  "set_count": 3,
  "rep_count": 12,
  "description": "..."
}
```

---
