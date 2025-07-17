# Tracker Workout Resource

Represents a workout record in the tracker system.


---

## Schema
| Field                   | Type    | Description                                 |
|-------------------------|---------|---------------------------------------------|
| `id`                    | integer | Workout record ID                           |
| `user_id`               | integer | User ID                                     |
| `start`                 | string  | Start datetime (YYYY-MM-DD HH:MM:SS)        |
| `workout_plan_session_id`| integer | Workout plan session ID (if applicable)     |
| `notes`                 | string  | Notes                                       |
| `end`                   | string  | End datetime (YYYY-MM-DD HH:MM:SS)          |

---

## Example
```
{
  "id": 123,
  "user_id": 123,
  "start": "2020-01-01 00:00:00",
  "workout_plan_session_id": 123,
  "notes": "...",
  "end": "2020-01-01 00:00:00"
}
```

---
