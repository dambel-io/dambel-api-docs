# POST /api/v1/users

Create a new user in the system.


---

## Permissions
| Permission     | Description  |
|----------------|--------------|
| `users.create` | Create users |

---

## Request Body Parameters
| Name         | Type    | Required | Description                         |
|--------------|---------|----------|-------------------------------------|
| `first_name` | string  | No       | First name (max 255)                |
| `last_name`  | string  | No       | Last name (max 255)                 |
| `email`      | string  | No       | Email (max 255, unique)             |
| `phone`      | string  | Yes      | Phone number (unique, E.164 format) |
| `username`   | string  | Yes      | Username (max 255, unique)          |
| `height`     | integer | No       | User's height in CM                 |
| `birth_date` | date    | No       | User's birth date                   |
| `password`   | string  | Yes      | Password (will be hashed)           |

---

## Response

### 200 OK
Returns the created user resource.

```json
{
  "data": { /* user resource */ }
}
```

See [User Resource](user_resource.md).

---

## Error Responses
| Status | Description                  | Reference                                                    |
|--------|------------------------------|--------------------------------------------------------------|
| 409    | Email or phone already in use|                                                              |
| 422    | Validation error             | [Validation error](../_globals/validation-errors.md)         |
| 401    | Unauthorized                 | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden                    | [Permission error](../_globals/permission-errors.md)         |
