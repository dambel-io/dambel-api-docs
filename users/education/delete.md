# `DELETE /api/v1/users/{user-id}/education/{education-id}`

Delete an education record from a user.


---

## Permissions
| Permission             | Description                                 |
|------------------------|---------------------------------------------|
| `education.delete`     | Delete your own education                   |
| `education.delete_any` | Delete education from any user              |

---

## Response

### 204 No Content
No content is returned when the education record is deleted successfully.

---

## Error Responses
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)
- **404 Not Found:** [Not-found error](../../_globals/not-found-errors.md)

---
