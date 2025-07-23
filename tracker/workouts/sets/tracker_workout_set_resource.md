# Tracker Workout Set Resource

Represents a workout set record in the tracker system.


---

## Schema
| Field                    | Type    | Description                                 |
|--------------------------|---------|---------------------------------------------|
| `id`                     | integer | Workout set record ID                       |
| `user_id`                | integer | User ID                                     |
| `start`                  | string  | Start datetime (YYYY-MM-DD HH:MM:SS)        |
| `workout_plan_exercise_id`| integer | Workout plan exercise ID (if applicable)    |
| `exercise_id`            | integer | Exercise ID                                 |
| `is_replacement`         | boolean | Whether this set is a replacement           |
| `rep_count`              | integer | Number of repetitions                       |
| `weight`                 | integer | Weight used                                 |
| `notes`                  | string  | Notes                                       |
| `end`                    | string  | End datetime (YYYY-MM-DD HH:MM:SS)          |

---

## Example
```json
{
  "id": 123,
  "user_id": 123,
  "start": "2020-01-01 00:00:00",
  "workout_plan_exercise_id": 123,
  "exercise_id": 123,
  "is_replacement": false,
  "rep_count": 10,
  "weight": 100,
  "notes": "...",
  "end": "2020-01-01 00:00:00"
}
```

---
