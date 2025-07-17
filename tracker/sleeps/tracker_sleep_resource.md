# Tracker Sleep Resource

Represents a sleep record in the tracker system.


---

## Schema
| Field         | Type    | Description                                 |
|--------------|---------|---------------------------------------------|
| `id`         | integer | Sleep record ID                             |
| `user_id`    | integer | User ID                                     |
| `tracked_at` | string  | Datetime of the sleep record (YYYY-MM-DD HH:MM:SS) |
| `notes`      | string  | Notes                                       |

---

## Example
```
{
  "id": 123,
  "user_id": 123,
  "tracked_at": "2020-01-01 00:00:00",
  "notes": "..."
}
```

---
