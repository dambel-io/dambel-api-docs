# Tracker Water Resource

Represents a water intake record in the tracker system.


---

## Schema
| Field         | Type    | Description                                 |
|--------------|---------|---------------------------------------------|
| `id`         | integer | Water record ID                             |
| `user_id`    | integer | User ID                                     |
| `tracked_at` | string  | Datetime of the water intake (YYYY-MM-DD HH:MM:SS) |
| `glass_count`| float   | Number of glasses                           |
| `notes`      | string  | Notes                                       |

---

## Example
```
{
  "id": 123,
  "user_id": 123,
  "tracked_at": "2020-01-01 00:00:00",
  "glass_count": 1.5,
  "notes": "..."
}
```

---
