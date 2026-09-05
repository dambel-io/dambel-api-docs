# PUT /api/v1/tracker/progress-photos/{tracker-progress-photo-id}

Update a progress-photo entry.


---

## Permissions
| Permission                        | Description                   |
|-----------------------------------|-------------------------------|
| `tracker_progress_photos.update`  | Update tracker progress photo |

Only the athlete who logged the entry may update it. A share viewer can *read* an entry (and its
image) but gets 403 here — viewers are strictly read-only.

---

## Request Body Parameters
| Name         | Type    | Required | Description                                          |
|--------------|---------|----------|------------------------------------------------------|
| `tracked_at` | string  | No       | Datetime the photo was taken                         |
| `pose`       | string  | No       | One of `front`, `side`, `back`, `other`. Nullable.   |
| `notes`      | string  | No       | Optional notes (max 2000 characters)                 |

*All parameters are optional. If omitted, they will not be updated. `pose` and `notes` may be set to `null`.*

Images are added and removed through [`POST /api/v1/media`](../../media/create.md) and
[`DELETE /api/v1/media/{media-id}`](../../media/delete.md), not here.

---

## Response

### 200 OK
```json
{
  "data": { /* tracker progress photo resource */ }
}
```
- See [Tracker Progress Photo Resource](tracker_progress_photo_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 422    | Validation Error   | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not Found          | [Not found error](../../_globals/not-found-errors.md)           |

---
