# Trainee Resource

Represents a trainee record in the system.


---

## Schema
| Field                | Type                              | Description                        |
|----------------------|-----------------------------------|------------------------------------|
| `id`                 | integer                           | Trainee record ID                  |
| `user_id`            | integer                           | Trainee user ID                    |
| `user`               | [UserResource](../../users/user_resource.md) | User resource (when loaded)        |
| `trainer_id`         | integer                           | Trainer user ID                    |
| `trainer`            | [UserResource](../../users/user_resource.md) | Trainer user resource (when loaded)|
| `training_service_id`| integer                           | Training service ID                |
| `training_service`   | [TrainingServiceResource](../services/training_service_resource.md) | Training service resource (when loaded) |
| `notes`              | string                            | Notes                              |
| `is_delivered`       | boolean                           | Whether the service is delivered   |

---

## Example
```json
{
  "id": 123,
  "user_id": 123,
  "user": <user resource>,
  "trainer_id": 123,
  "trainer": <user resource>,
  "training_service_id": 123,
  "training_service": <training service resource>,
  "notes": "...",
  "is_delivered": false
}
```

---
