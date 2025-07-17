# GET /api/v1/tracker/sleeps

Retrieve a list of sleep records in the tracker system.


---

## Permissions
| Permission             | Description                |
|------------------------|----------------------------|
| `tracker_sleeps.view`  | View tracker sleep records |

---

## Query Parameters
| Name                | Type    | Required | Description                                                      |
|---------------------|---------|----------|------------------------------------------------------------------|
| `start_date`        | string  | No       | Start of the date range (YYYY-MM-DD)                             |
| `end_date`          | string  | No       | End of the date range (YYYY-MM-DD)                               |
| `shared_tracker_slug`| string | No       | Slug of a shared tracker record (default: your own data)         |
| `search`            | string  | No       | Search by notes                                                  |
| `page`              | int     | No       | Page number for pagination                                       |

---

## Response

### 200 OK
```
{
  "data": [<tracker sleep resource>, ...],
  "links": {<pagination data>},
  "meta": {<pagination data>}
}
```
- See [Tracker Sleep Resource](tracker_sleep_resource.md)
- See [Pagination Data](../../_globals/pagination-data.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
