# DELETE /api/v1/tracker/sleeps/{tracker-sleep-id}

Delete a sleep record in the tracker system.


---

## Permissions
| Permission                | Description                |
|---------------------------|----------------------------|
| `tracker_sleeps.delete`   | Delete tracker sleep       |

---

## Request Body Parameters
_None._

---

## Response

### 204 No Content
No content is returned when the sleep record is deleted successfully.

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
