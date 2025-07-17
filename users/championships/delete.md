# `DELETE /api/v1/users/{user-id}/championships/{championship-id}`

Delete a championship record from a user.


---

## Permissions
| Permission                  | Description                                 |
|-----------------------------|---------------------------------------------|
| `championships.delete`      | Delete your own championships               |
| `championships.delete_any`  | Delete championships from any user          |

---

## Response

### 204 No Content
No content is returned when the championship record is deleted successfully.

---

## Error Responses
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)
- **404 Not Found:** [Not-found error](../../_globals/not-found-errors.md)

---
