# Trainee Resource

Represents a trainee record in the system.


---

## Schema
| Field                | Type    | Description                        |
|----------------------|---------|------------------------------------|
| `id`                 | integer | Trainee record ID                  |
| `user_id`            | integer | Trainee user ID                    |
| `trainer_id`         | integer | Trainer user ID                    |
| `trainer_service_id` | integer | Training service ID                |
| `notes`              | string  | Notes                              |
| `is_delivered`       | boolean | Whether the service is delivered   |

---

## Example
```json
{
  "id": 123,
  "user_id": 123,
  "trainer_id": 123,
  "trainer_service_id": 123,
  "notes": "...",
  "is_delivered": false
}
```

---
