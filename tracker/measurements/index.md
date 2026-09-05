# GET /api/v1/tracker/measurements

Retrieve a list of body-measurement records in the tracker system.


---

## Permissions
| Permission                     | Description                      |
|--------------------------------|----------------------------------|
| `tracker_measurements.view`    | View tracker measurement records |

---

## Query Parameters
| Name                | Type    | Required | Description                                                      |
|---------------------|---------|----------|------------------------------------------------------------------|
| `start_date`        | string  | No       | Start of the date range (YYYY-MM-DD)                             |
| `end_date`          | string  | No       | End of the date range (YYYY-MM-DD)                               |
| `shared_tracker_id` | string  | No       | ID of a shared tracker record (default: your own data). A share the caller is not party to, or one that does not exist, returns 404 — the two are indistinguishable. A share whose `include_measurement` is `false` returns an **empty list**, never the caller's own rows. |
| `search`            | string  | No       | Search by notes                                                  |
| `page`              | int     | No       | Page number for pagination                                       |
| `per_page`          | int     | No       | Rows per page, 1-100 (default: 50). Values outside that range are rejected with 422. |

Results are ordered by `tracked_at` descending, 50 per page by default.

`start_date`, `end_date`, `search` and `per_page` are validated; an out-of-range `per_page` or a
malformed date is a 422 naming the field rather than a silently ignored filter.

---

## Response

### 200 OK
```json
{
  "data": [<tracker measurement resource>, ...],
  "links": {<pagination data>},
  "meta": {<pagination data>}
}
```
- See [Tracker Measurement Resource](tracker_measurement_resource.md)
- See [Pagination Data](../../_globals/pagination-data.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |
| 404    | `shared_tracker_id` names a share the caller may not read | [Not found error](../../_globals/not-found-errors.md) |

---
