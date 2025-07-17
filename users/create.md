# `POST /api/v1/users`

Create a new user in the system.


---

## Permissions
| Permission      | Description         |
|-----------------|---------------------|
| `users.create`  | Create users        |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                 |
|--------------|---------|----------|---------------------------------------------|
| `first_name` | string  | Yes      | First name (max 255)                        |
| `last_name`  | string  | Yes      | Last name (max 255)                         |
| `email`      | string  | Yes      | Email (max 255, unique)                     |
| `phone`      | string  | Yes      | Phone number (max 255, unique)              |
| `password`   | string  | Yes      | Password (will be hashed and saved)         |

---

## Response

### 201 Created
```
{
  "user": {<user resource>}
}
```
- [User Resource](user_resource.md)

---

## Error Responses
- **409 Conflict:** Email/Phone already in use
- **422 Unprocessable Entity:** [Validation error](../_globals/validation-errors.md)
- **401 Unauthorized:** [Authentication error](../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../_globals/permission-errors.md)

---
