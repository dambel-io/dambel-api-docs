# Tracker Weight Resource

Represents a weight record in the tracker system.


---

## Schema
| Field         | Type    | Description                                 |
|--------------|---------|---------------------------------------------|
| `id`         | integer | Weight record ID                            |
| `user_id`    | integer | User ID                                     |
| `tracked_at` | string  | Datetime of the weight record (YYYY-MM-DD HH:MM:SS) |
| `weight`     | float   | Weight in kilograms (kg)                     |
| `notes`      | string  | Notes                                       |

---

## Example
```
{
  "id": 123,
  "user_id": 123,
  "tracked_at": "2020-01-01 00:00:00",
  "weight": 70.0,
  "notes": "..."
}
```

---
