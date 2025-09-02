# PUT /api/v1/tracker/shares/{sharedTracker}

Update an existing shared tracker configuration.


---

## Permissions
| Permission                 | Description                |
|----------------------------|----------------------------|
| `shared_trackers.update`   | Update shared tracker      |
| `shared_trackers.view`     | View shared tracker        |

---

## URL Parameters
| Name            | Type    | Required | Description                    |
|-----------------|---------|----------|--------------------------------|
| `sharedTracker` | integer | Yes      | ID of the shared tracker to update |

---

## Request Body Parameters
| Name                | Type    | Required | Description                                                                 |
|---------------------|---------|----------|-----------------------------------------------------------------------------|
| `start_date`       | string  | No       | Start date for the sharing period (YYYY-MM-DD format)                     |
| `end_date`         | string  | No       | End date for the sharing period (YYYY-MM-DD format)                       |
| `include_wakeup`   | boolean | No       | Whether to include wakeup data                                             |
| `include_weight`   | boolean | No       | Whether to include weight data                                             |
| `include_water`    | boolean | No       | Whether to include water intake data                                       |
| `include_sleep`    | boolean | No       | Whether to include sleep data                                              |
| `include_supplement` | boolean | No       | Whether to include supplement data                                         |
| `include_meal`     | boolean | No       | Whether to include meal data                                               |
| `include_workout`  | boolean | No       | Whether to include workout data                                            |
| `notify_wakeup`    | boolean | No       | Whether to notify the viewer about new wakeup data                         |
| `notify_weight`    | boolean | No       | Whether to notify the viewer about new weight data                         |
| `notify_water`     | boolean | No       | Whether to notify the viewer about new water intake data                   |
| `notify_sleep`     | boolean | No       | Whether to notify the viewer about new sleep data                          |
| `notify_supplement` | boolean | No       | Whether to notify the viewer about new supplement data                     |
| `notify_meal`      | boolean | No       | Whether to notify the viewer about new meal data                           |
| `notify_workout`   | boolean | No       | Whether to notify the viewer about new workout data                        |
| `description`      | string  | No       | Optional description for the shared tracker (max: 2000 characters)        |

**Note:** If both `start_date` and `end_date` are provided, `end_date` must be after `start_date`.

**Note:** The viewer user can only change `notify_*` fields.

**Note:** The owner user can only change all fields EXCEPT `notify_*` fields.

---

## Response

### 200 OK
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
| 404    | Not Found          | [Not found error](../../_globals/not-found-errors.md)           |

---

## Example Request

```bash
curl -X PUT "https://api.example.com/api/v1/tracker/shares/1" \
  -H "Authorization: Bearer {token}" \
  -H "Content-Type: application/json" \
  -d '{
    "description": "Updated January fitness tracking data",
    "include_weight": true,
    "notify_workout": true
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

- Users can only update shared trackers where they are either the owner (`user_id`) or the viewer (`viewer_user_id`)
- Only the fields provided in the request will be updated
- The `user_id` and `viewer_user_id` fields cannot be modified
- Partial updates are supported - only include the fields you want to change
- The `end_date` validation rule only applies when both `start_date` and `end_date` are provided
