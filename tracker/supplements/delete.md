# DELETE /api/v1/tracker/supplements/{tracker-supplement-id}

Delete a supplement record in the tracker system.


---

## Permissions
| Permission                      | Description                      |
|----------------------------------|----------------------------------|
| `tracker_supplements.delete`     | Delete tracker supplement record |

---

## Request Body Parameters
_None._

---

## Response

### 204 No Content
No content is returned when the supplement record is deleted successfully.

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
