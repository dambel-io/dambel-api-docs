# `DELETE /api/v1/users/{user-id}/detach-role/{role-id}`

Detach a role from a user.


---

## Permissions
| Permission            | Description                                  |
|-----------------------|----------------------------------------------|
| `users.detach_role`   | Detach a role from any user except themselves|

---

## Response

### 204 No Content
```
{
  "message": "Role detached successfully"
}
```

---

## Error Responses
- **400 Bad Request:**
  - User does not have this role
  ```
  {
    "error": "User does not have this role"
  }
  ```
- **401 Unauthorized:** [Authentication error](../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../_globals/permission-errors.md)
- **404 Not Found:** Role or user not found ([Not-found error](../_globals/not-found-errors.md))

---
