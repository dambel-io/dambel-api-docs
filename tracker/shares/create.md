# POST /api/v1/tracker/shares

Create a new shared tracker configuration to share tracker data with another user.


---

## Permissions
| Permission                 | Description                |
|----------------------------|----------------------------|
| `shared_trackers.create`   | Create shared tracker      |

---

## Request Body Parameters
| Name                | Type    | Required | Description                                                                 |
|---------------------|---------|----------|-----------------------------------------------------------------------------|
| `viewer_user_id`   | integer | Yes      | ID of the user to share tracker data with                                 |
| `start_date`       | string  | No       | Start date for the sharing period (YYYY-MM-DD format) or null             |
| `end_date`         | string  | No       | End date for the sharing period (YYYY-MM-DD format) or null               |
| `include_wakeup`   | boolean | No       | Whether to include wakeup data (default: true)                            |
| `include_weight`   | boolean | No       | Whether to include weight data (default: true)                            |
| `include_water`    | boolean | No       | Whether to include water intake data (default: true)                      |
| `include_sleep`    | boolean | No       | Whether to include sleep data (default: true)                             |
| `include_supplement` | boolean | No       | Whether to include supplement data (default: true)                        |
| `include_meal`     | boolean | No       | Whether to include meal data (default: true)                              |
| `include_workout`  | boolean | No       | Whether to include workout data (default: true)                           |
| `description`      | string  | No       | Optional description for the shared tracker (max: 2000 characters)        |

---

## Response

### 201 Created
```
<shared tracker resource>
```
- See [Shared Tracker Resource](shared_tracker_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 422    | Validation Error   | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---

## Example Request

```bash
curl -X POST "https://api.example.com/api/v1/tracker/shares" \
  -H "Authorization: Bearer {token}" \
  -H "Content-Type: application/json" \
  -d '{
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
  }'
```

## Example Response

```json
{
  "data": <shared tracker resource>
}
```

See [Shared Tracker Resource](shared_tracker_resource.md) for the complete response structure.

---

## Notes

- The `user_id` is automatically set to the authenticated user's ID
- All `include_*` flags default to `true` if not specified
- All `notify_*` flags default to `false` if not specified
- If both `start_date` and `end_date` are provided, `end_date` must be after `start_date`
- The `viewer_user_id` must reference an existing user
- When `start_date` and `end_date` are `null`, all tracker data is shared without date restrictions
