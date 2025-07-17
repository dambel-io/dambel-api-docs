# `POST /api/v1/users/{user-id}/attach-role/{role-id}`

Attach a role to a user.


---

## Permissions
| Permission           | Description                                 |
|----------------------|---------------------------------------------|
| `users.attach_role`  | Attach a role to any user except themselves |

---

## Response

### 201 Created
```
{
  "message": "Role attached successfully"
}
```

---

## Error Responses
- **400 Bad Request:**
  - User already has this role
  ```
  {
    "error": "User already has this role"
  }
  ```
- **401 Unauthorized:** [Authentication error](../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../_globals/permission-errors.md)
- **404 Not Found:** Role or user not found ([Not-found error](../_globals/not-found-errors.md))

---
