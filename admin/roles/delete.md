# `DELETE /api/v1/admin/roles/{role-id}`

Delete a role.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `roles.view_all`      | Access roles        |
| `roles.delete`        | Delete role         |

---

## Response

### 204 No Content
No content is returned when the role is deleted successfully.

---

## Error Responses
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)
- **404 Not Found:** [Not-found error](../../_globals/not-found-errors.md)

---
