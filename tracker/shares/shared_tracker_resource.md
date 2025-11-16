# Shared Tracker Resource

The shared tracker resource represents a shared tracker configuration between two users.

---

## Resource Structure

| Field              | Type    | Description                                                                 |
|--------------------|---------|-----------------------------------------------------------------------------|
| `id`               | integer | Unique identifier for the shared tracker                                   |
| `user_id`          | integer | ID of the user who is sharing their tracker data                          |
| `user`          | [UserResource](../../users/user_resource.md) | User object                          |
| `viewer_user_id`   | integer | ID of the user who can view the shared tracker data                       |
| `viewer_user`          | [UserResource](../../users/user_resource.md) | Viewer user object                          |
| `start_date`       | string  | Start date for the sharing period (YYYY-MM-DD format) or null             |
| `end_date`         | string  | End date for the sharing period (YYYY-MM-DD format) or null               |
| `include_wakeup`   | boolean | Whether wakeup data is included in the shared tracker                     |
| `include_weight`   | boolean | Whether weight data is included in the shared tracker                     |
| `include_water`    | boolean | Whether water intake data is included in the shared tracker               |
| `include_sleep`    | boolean | Whether sleep data is included in the shared tracker                      |
| `include_supplement` | boolean | Whether supplement data is included in the shared tracker                 |
| `include_meal`     | boolean | Whether meal data is included in the shared tracker                       |
| `include_workout`  | boolean | Whether workout data is included in the shared tracker                    |
| `notify_wakeup`    | boolean | Whether to notify the viewer about new wakeup data                        |
| `notify_weight`    | boolean | Whether to notify the viewer about new weight data                        |
| `notify_water`     | boolean | Whether to notify the viewer about new water intake data                  |
| `notify_sleep`     | boolean | Whether to notify the viewer about new sleep data                         |
| `notify_supplement` | boolean | Whether to notify the viewer about new supplement data                    |
| `notify_meal`      | boolean | Whether to notify the viewer about new meal data                          |
| `notify_workout`   | boolean | Whether to notify the viewer about new workout data                       |
| `description`      | string  | Optional description for the shared tracker                               |
| `created_at`       | string  | Timestamp when the shared tracker was created                             |
| `updated_at`       | string  | Timestamp when the shared tracker was last updated                        |

**Note:** `start_date` and `end_date` can be `null`, indicating no date restrictions for the shared tracker data.

---

## Example Response

```json
{
  "data": {
    "id": 1,
    "user_id": 123,
    "viewer_user_id": 456,
    "start_date": "2024-01-01",
    "end_date": "2024-01-31",
    "include_wakeup": true,
    "include_weight": true,
    "include_water": true,
    "include_sleep": true,
    "include_supplement": false,
    "include_meal": true,
    "include_workout": true,
    "notify_wakeup": false,
    "notify_weight": false,
    "notify_water": false,
    "notify_sleep": false,
    "notify_supplement": false,
    "notify_meal": false,
    "notify_workout": false,
    "description": "January fitness tracking data",
    "created_at": "2024-01-01T00:00:00.000000Z",
    "updated_at": "2024-01-01T00:00:00.000000Z"
  }
}
```

---

## Related Resources

- [Create Shared Tracker](create.md)
- [List Shared Trackers](index.md)
- [Update Shared Tracker](update.md)
- [Delete Shared Tracker](delete.md)
