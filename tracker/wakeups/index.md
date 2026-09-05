# GET /api/v1/tracker/wakeups

List wake-up records — your own, or those of a tracker shared with you.


---

## Permissions
| Permission              | Description                 |
|-------------------------|-----------------------------|
| `tracker_wakeups.view`  | View wake-up records        |

---

## Query Parameters
| Name                | Type   | Required | Description                                                                                     |
|---------------------|--------|----------|-------------------------------------------------------------------------------------------------|
| `start_date`        | date   | No       | Only records tracked on or after this date                                                      |
| `end_date`          | date   | No       | Only records tracked on or before this date                                                     |
| `shared_tracker_id` | int    | No       | Read another user's records through a shared tracker. A share the caller is not party to, or one that does not exist, returns 404 — the two are indistinguishable |
| `search`            | string | No       | Match against `notes`                                                                           |
| `page`              | int    | No       | Page number                                                                                     |

---

## Request Example
```
GET /api/v1/tracker/wakeups?start_date=2026-08-01&end_date=2026-08-31&page=1
```

---

## Response

### 200 OK
Ordered by `tracked_at` descending.

```json
{
  "data": [<tracker wakeup resource>, ...],
  "links": {<pagination data>},
  "meta": {<pagination data>}
}
```
- [Tracker Wakeup Resource](tracker_wakeup_resource.md)
- [Pagination Data](../../_globals/pagination-data.md) (per page: 100, not client-controllable)

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |
| 404    | `shared_tracker_id` names a share the caller may not read | [Not found error](../../_globals/not-found-errors.md) |

---
