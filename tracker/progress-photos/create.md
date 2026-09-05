# POST /api/v1/tracker/progress-photos

Record a new progress-photo entry.


---

## Permissions
| Permission                        | Description                   |
|-----------------------------------|-------------------------------|
| `tracker_progress_photos.create`  | Create tracker progress photo |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                          |
|--------------|---------|----------|------------------------------------------------------|
| `tracked_at` | string  | Yes      | Datetime the photo was taken                         |
| `pose`       | string  | No       | One of `front`, `side`, `back`, `other`. Nullable.   |
| `notes`      | string  | No       | Optional notes (max 2000 characters)                 |

**The image is not part of this request.** Create the entry first, then attach the file with a
second call to [`POST /api/v1/media`](../../media/create.md) using
`attachable_type=tracker_progress_photo` and the returned `id` as `attachable_id` — the same
two-step flow a meal photo uses. Attaching is authorized by `update` on the entry, so only its
owner can add an image to it.

`user_id` is taken from the authenticated token and is never read from the request body.

---

## Response

### 201 Created
```json
{
  "data": { /* tracker progress photo resource, with an empty `media` array */ }
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

---
