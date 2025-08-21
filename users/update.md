# `PUT /api/v1/users/{user-id}`

Update the information of a specific user.


---

## Permissions
| Permission         | Description                        |
|--------------------|------------------------------------|
| `users.update_any` | Update any user as an admin        |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                             |
|--------------|---------|----------|---------------------------------------------------------|
| `first_name` | string  | No       | First name (max 255)                                    |
| `last_name`  | string  | No       | Last name (max 255)                                     |
| `email`      | string  | No       | Email (max 255, unique)                                 |
| `phone`      | string  | No       | Phone number (max 255, unique)                          |
| `username`   | string  | No       | Username (max 255, unique)                              |
| `height`     | integer | No       | User's height in CM                                     |
| `birth_date` | date    | No       | User's birth date                                       |
| `password`   | string  | No       | New password (will be hashed and saved)                 |

*All parameters are optional. If omitted, they will not be updated. Required fields cannot be set to null.*

---

## Response

### 200 OK
```json
{
  "user": {<user resource>}
}
```
- [User Resource](user_resource.md)

---

## Error Responses
- **404 Not Found:** Wrong user ID passed
- **409 Conflict:** Newly set email/phone is already in use
- **422 Unprocessable Entity:** [Validation error](../_globals/validation-errors.md)
- **401 Unauthorized:** [Authentication error](../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../_globals/permission-errors.md)

---
