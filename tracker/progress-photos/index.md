# GET /api/v1/tracker/progress-photos

Retrieve a list of progress-photo records in the tracker system.


---

## Permissions
| Permission                        | Description                        |
|-----------------------------------|------------------------------------|
| `tracker_progress_photos.view`    | View tracker progress-photo records |

---

## Query Parameters
| Name                | Type    | Required | Description                                                      |
|---------------------|---------|----------|------------------------------------------------------------------|
| `start_date`        | string  | No       | Start of the date range (YYYY-MM-DD)                             |
| `end_date`          | string  | No       | End of the date range (YYYY-MM-DD)                               |
| `pose`              | string  | No       | Filter by pose: `front`, `side`, `back`, `other`                 |
| `shared_tracker_id` | string  | No       | ID of a shared tracker record (default: your own data). A share the caller is not party to, or one that does not exist, returns 404 — the two are indistinguishable. A share whose `include_progress_photo` is `false` returns an **empty list**, never the caller's own rows. |
| `search`            | string  | No       | Search by notes                                                  |
| `page`              | int     | No       | Page number for pagination                                       |
| `per_page`          | int     | No       | Rows per page, 1-100 (default: 50). Values outside that range are rejected with 422. |

Results are ordered by `tracked_at` descending, 50 per page by default. Attached images are
eager-loaded, so the query count does not grow with the size of the page.

`start_date`, `end_date`, `search`, `pose` and `per_page` are validated; an unknown `pose`, an
out-of-range `per_page` or a malformed date is a 422 naming the field rather than a silently
ignored filter.

**`include_progress_photo` defaults to `false` on a new share** — the only `include_*` flag that
does. A viewer sees nothing here until the athlete turns it on deliberately.

---

## Response

### 200 OK
```json
{
  "data": [<tracker progress photo resource>, ...],
  "links": {<pagination data>},
  "meta": {<pagination data>}
}
```
- See [Tracker Progress Photo Resource](tracker_progress_photo_resource.md)
- See [Pagination Data](../../_globals/pagination-data.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |
| 404    | `shared_tracker_id` names a share the caller may not read | [Not found error](../../_globals/not-found-errors.md) |

---
