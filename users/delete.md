# `DELETE /api/v1/users/{user-id}`

Delete a user from the system.


---

## Permissions
| Permission         | Description           |
|--------------------|----------------------|
| `users.delete_any` | Delete any user      |

---

## Response

### 204 No Content
No content is returned when the user is deleted successfully.

---

## Error Responses
- **401 Unauthorized:** [Authentication error](../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../_globals/permission-errors.md)
- **404 Not Found:** [Not-found error](../_globals/not-found-errors.md)

---
