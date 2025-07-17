# Workout Plan Resource

Represents a workout plan in the system.


---

## Schema
| Field         | Type    | Description                                 |
|-------------- |---------|---------------------------------------------|
| `id`          | integer | Workout plan ID                             |
| `user_id`     | integer | User ID (creator)                           |
| `trainee_id`  | integer | Trainee ID                                  |
| `title`       | string  | Title                                       |
| `description` | string  | Description                                 |
| `created_at`  | string  | Creation timestamp                          |
| `sessions`    | array   | List of [Workout Plan Session Resource](sessions/workout_plan_session_resource.md) |

---

## Example
```
{
  "id": 123,
  "user_id": 123,
  "trainee_id": 123,
  "title": "...",
  "description": "...",
  "created_at": "2020-01-01 00:00:00",
  "sessions": [<workout plan session resource>]
}
```

---

## Related Resources
- [Workout Plan Session Resource](sessions/workout_plan_session_resource.md)

---
