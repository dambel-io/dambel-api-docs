# Workout Plan Session Resource

Represents a session in a workout plan.


---

## Schema
| Field             | Type    | Description                      |
|-------------------|---------|----------------------------------|
| `id`              | integer | Session ID                       |
| `workout_plan_id` | integer | Associated workout plan ID        |
| `title`           | string  | Title of the session             |
| `day`             | string  | Weekday of the session           |
| `description`     | string  | Description                      |

---

## Example
```
{
  "id": 123,
  "workout_plan_id": 123,
  "title": "Leg Day",
  "day": "saturday",
  "description": "Lower body workout"
}
```

---
