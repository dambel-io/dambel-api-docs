# POST /api/v1/tracker/shares

Create a new shared tracker configuration to share tracker data with another user.


---

## Permissions
| Permission               | Description             |
|--------------------------|-------------------------|
| `shared_trackers.create` | Create shared tracker   |

---

## Request Body Parameters
| Name                 | Type    | Required | Description                                                         |
|----------------------|---------|----------|---------------------------------------------------------------------|
| `viewer_user_id`     | integer | Yes      | ID of the user to share tracker data with                           |
| `start_date`         | string  | No       | Start date for the sharing period (YYYY-MM-DD) or null              |
| `end_date`           | string  | No       | End date for the sharing period (YYYY-MM-DD) or null                |
| `include_wakeup`     | boolean | No       | Whether to include wakeup data (default: true)                      |
| `include_weight`     | boolean | No       | Whether to include weight data (default: true)                      |
| `include_water`      | boolean | No       | Whether to include water intake data (default: true)                |
| `include_sleep`      | boolean | No       | Whether to include sleep data (default: true)                       |
| `include_supplement` | boolean | No       | Whether to include supplement data (default: true)                  |
| `include_meal`       | boolean | No       | Whether to include meal data (default: true)                        |
| `include_workout`    | boolean | No       | Whether to include workout data (default: true)                     |
| `notify_wakeup`      | boolean | No       | Whether to notify when the owner logs a wakeup (default: false)     |
| `notify_weight`      | boolean | No       | Whether to notify when the owner logs their weight (default: false)  |
| `notify_water`       | boolean | No       | Whether to notify when the owner logs water intake (default: false) |
| `notify_sleep`       | boolean | No       | Whether to notify when the owner logs sleep (default: false)        |
| `notify_supplement`  | boolean | No       | Whether to notify when the owner logs a supplement (default: false) |
| `notify_meal`        | boolean | No       | Whether to notify when the owner logs a meal (default: false)       |
| `notify_workout`     | boolean | No       | Whether to notify when the owner logs a workout (default: false)    |
| `description`        | string  | No       | Optional description for the shared tracker (max 2000 characters)   |

> **Note:** If both `start_date` and `end_date` are provided, `end_date` must be after `start_date`. When both are `null`, all tracker data is shared without date restrictions.

---

## Request Example
```json
{
  "viewer_user_id": 456,
  "start_date": "2024-01-01",
  "end_date": "2024-01-31",
  "description": "January fitness tracking data",
  "include_wakeup": true,
  "include_weight": false,
  "include_water": true,
  "include_sleep": true,
  "include_supplement": false,
  "include_meal": true,
  "include_workout": true
}
```

---

## Response

### 200 OK
Returns the created shared tracker resource.

```json
{ /* shared tracker resource */ }
```

See [Shared Tracker Resource](shared_tracker_resource.md).

---

## Error Responses
| Status | Description       | Reference                                                       |
|--------|-------------------|-----------------------------------------------------------------|
| 422    | Validation error  | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized      | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden         | [Permission error](../../_globals/permission-errors.md)         |
