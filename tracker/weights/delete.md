# DELETE /api/v1/tracker/weights/{tracker-weight-id}

Delete a weight record in the tracker system.


---

## Permissions
| Permission                 | Description                |
|----------------------------|----------------------------|
| `tracker_weights.delete`   | Delete tracker weight      |

---

## Request Body Parameters
_None._

---

## Response

### 204 No Content
No content is returned when the weight record is deleted successfully.

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
