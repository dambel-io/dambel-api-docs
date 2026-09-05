# DELETE /api/v1/tracker/measurements/{tracker-measurement-id}

Delete a body-measurement record.


---

## Permissions
| Permission                     | Description                |
|--------------------------------|----------------------------|
| `tracker_measurements.delete`  | Delete tracker measurement |

Only the athlete who logged the record may delete it. Share viewers are strictly read-only.

---

## Request Body Parameters
_None._

---

## Response

### 204 No Content
No body. The deletion is permanent — there are no soft deletes anywhere in this codebase.

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not Found          | [Not found error](../../_globals/not-found-errors.md)           |

---
