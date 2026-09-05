# DELETE /api/v1/tracker/progress-photos/{tracker-progress-photo-id}

Delete a progress-photo entry.


---

## Permissions
| Permission                        | Description                   |
|-----------------------------------|-------------------------------|
| `tracker_progress_photos.delete`  | Delete tracker progress photo |

Only the athlete who logged the entry may delete it. Share viewers are strictly read-only.

---

## Request Body Parameters
_None._

---

## Response

### 204 No Content
No body. The deletion is permanent — there are no soft deletes anywhere in this codebase.

**Deleting an entry deletes its attached `media` rows with it**, so the image URL stops resolving
(404) rather than merely becoming unauthorized. `media.attachable` is polymorphic and has no
foreign key, so this is done by a model event rather than a database cascade — which means it
does **not** happen when the rows are removed by the `users` cascade on account deletion.

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not Found          | [Not found error](../../_globals/not-found-errors.md)           |

---
