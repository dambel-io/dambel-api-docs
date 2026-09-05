# GET /api/v1/tracker/workouts

Retrieve a list of workout records in the tracker system.


---

## Permissions
| Permission               | Description                |
|--------------------------|----------------------------|
| `tracker_workouts.view`  | View tracker workouts      |

---

## Query Parameters
| Name                | Type    | Required | Description                                                      |
|---------------------|---------|----------|------------------------------------------------------------------|
| `start_date`        | string  | No       | Start of the date range (YYYY-MM-DD)                             |
| `end_date`          | string  | No       | End of the date range (YYYY-MM-DD)                               |
| `shared_tracker_id`| string | No       | ID of a shared tracker record (default: your own data). A share the caller is not party to, or one that does not exist, returns 404 — the two are indistinguishable. |
| `search`            | string  | No       | Search by notes                                                  |
| `page`              | int     | No       | Page number for pagination                                       |

---

## Response

### 200 OK
```json
{
  "data": [<tracker workout resource>, ...],
  "links": {<pagination data>},
  "meta": {<pagination data>}
}
```
- See [Tracker Workout Resource](tracker_workout_resource.md)
- See [Pagination Data](../../_globals/pagination-data.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |
| 404    | `shared_tracker_id` names a share the caller may not read | [Not found error](../../_globals/not-found-errors.md) |

---
