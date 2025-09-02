# GET /api/v1/tracker/shares

Retrieve a list of shared tracker configurations.


---

## Permissions
| Permission                 | Description                |
|----------------------------|----------------------------|
| `shared_trackers.view`     | View shared trackers       |

---

## Query Parameters
| Name                | Type    | Required | Description                                                                 |
|---------------------|---------|----------|-----------------------------------------------------------------------------|
| `user_id`          | integer | No       | Filter by user ID (person sharing the tracker)                              |
| `viewer_user_id`   | integer | No       | Filter by viewer user ID (person the tracker is shared with)                |
| `start_date`       | string  | No       | Filter by start date (YYYY-MM-DD format)                                   |
| `end_date`         | string  | No       | Filter by end date (YYYY-MM-DD format)                                     |
| `include_wakeup`   | boolean | No       | Filter by whether wakeup data is included                                  |
| `include_weight`   | boolean | No       | Filter by whether weight data is included                                  |
| `include_water`    | boolean | No       | Filter by whether water intake data is included                            |
| `include_sleep`    | boolean | No       | Filter by whether sleep data is included                                   |
| `include_supplement` | boolean | No       | Filter by whether supplement data is included                              |
| `include_meal`     | boolean | No       | Filter by whether meal data is included                                    |
| `include_workout`  | boolean | No       | Filter by whether workout data is included                                 |
| `search`           | string  | No       | Search in description field                                                 |
| `page`             | integer | No       | Page number for pagination (default: 1)                                    |
| `per_page`         | integer | No       | Number of items per page (default: 100)                                    |

---

## Response

### 200 OK
```
<shared tracker resource collection>
```
- See [Shared Tracker Resource](shared_tracker_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---

## Example Request

```bash
curl -X GET "https://api.example.com/api/v1/tracker/shares?user_id=123&include_wakeup=true&search=workout" \
  -H "Authorization: Bearer {token}"
```

## Example Response

```json
{
  "data": [
    <shared tracker resource>
  ],
  "current_page": 1,
  "per_page": 100,
  "total": 1
}
```

See [Shared Tracker Resource](shared_tracker_resource.md) for the complete resource structure.

---

## Notes

- Users can only see shared trackers where they are either the owner (`user_id`) or the viewer (`viewer_user_id`)
- Results are ordered by creation date (newest first)
- The response includes pagination information
- Boolean filters work with `true`/`false` values
- Date filters use the format `YYYY-MM-DD`
- Search is performed on the `description` field using partial matching
