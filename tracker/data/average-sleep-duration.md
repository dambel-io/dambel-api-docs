# GET /api/v1/tracker/data/average-sleep-duration

Retrieve your average sleep duration.


---

## Query Parameters
| Name                | Type    | Required | Description                                                      |
|---------------------|---------|----------|------------------------------------------------------------------|
| `start_date`        | string  | No       | Start of the date range (YYYY-MM-DD)                             |
| `end_date`          | string  | No       | End of the date range (YYYY-MM-DD)                               |
| `shared_tracker_id`| string | No       | ID of a shared tracker record (default: your own data)         |
| `search`            | string  | No       | Search by notes                                                  |

---

## Response

### 200 OK
```json
{
  "average_sleep_duration": "07:34"
}
```

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
