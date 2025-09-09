# GET /api/v1/tracker/data/averages

Retrieve your tracker averages.


---

## Query Parameters
| Name                | Type    | Required | Description                                                      |
|---------------------|---------|----------|------------------------------------------------------------------|
| `start_date`        | string  | No       | Start of the date range (YYYY-MM-DD)                             |
| `end_date`          | string  | No       | End of the date range (YYYY-MM-DD)                               |
| `shared_tracker_id`| string | No         | ID of a shared tracker record (default: your own data)           |
| `search`            | string  | No       | Search by notes                                                  |

---

## Response

### 200 OK
```json
{
  "average_sleep_duration": "07:34",
  "average_workout_duration": 94,
  "average_daily_protein": 210.7,
  "average_daily_carb": 346.1,
  "average_daily_fat": 50,
  "average_daily_calories": 3415.3,
  "average_daily_water": 4.1
}
```

- `average_workout_duration` is minutes.
- Average macros are in grams.
- `average_daily_water` is in liters.

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
