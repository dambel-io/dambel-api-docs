# PUT /api/v1/users/{user-id}

Update the information of a specific user.


---

## Permissions
| Permission         | Description                 |
|--------------------|-----------------------------|
| `users.update_any` | Update any user as an admin |

---

## Request Body Parameters
| Name         | Type    | Required | Description                             |
|--------------|---------|----------|-----------------------------------------|
| `first_name` | string  | No       | First name (max 255)                    |
| `last_name`  | string  | No       | Last name (max 255)                     |
| `email`      | string  | No       | Email (max 255, unique)                 |
| `phone`      | string  | No       | Phone number (unique, E.164 format)     |
| `username`   | string  | No       | Username (max 255, unique)              |
| `height`     | integer | No       | User's height in CM                     |
| `birth_date` | date    | No       | User's birth date                       |
| `password`   | string  | No       | New password (will be hashed)           |

*All parameters are optional. If omitted, they will not be updated.*

---

## Response

### 200 OK
Returns the updated user resource.

```json
{
  "data": { /* user resource */ }
}
```

See [User Resource](user_resource.md).

---

## Error Responses
| Status | Description                       | Reference                                                    |
|--------|-----------------------------------|--------------------------------------------------------------|
| 404    | User not found                    | [Not-found error](../_globals/not-found-errors.md)           |
| 409    | Email or phone already in use     |                                                              |
| 422    | Validation error                  | [Validation error](../_globals/validation-errors.md)         |
| 401    | Unauthorized                      | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden                         | [Permission error](../_globals/permission-errors.md)         |
