# DELETE /api/v1/tracker/meals/{tracker-meal-id}

Delete a meal record in the tracker system.


---

## Permissions
| Permission                   | Description                      |
|------------------------------|----------------------------------|
| `tracker_meals.delete`       | Delete tracker meal record       |

---

## Request Body Parameters
_None._

---

## Response

### 204 No Content
No content is returned when the meal record is deleted successfully.

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
