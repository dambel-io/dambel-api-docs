# PUT /api/v1/auth/change-password

Allows the currently authenticated user to change their password.


---

## Permissions
This endpoint requires authentication but does not require any special permissions. Users can only change their own password.

---

## Request Body Parameters
| Name               | Type   | Required | Description                                      |
|--------------------|--------|----------|--------------------------------------------------|
| `current_password` | string | Yes      | The user's current password                      |
| `password`         | string | Yes      | The new password (minimum 8 characters)         |
| `password_confirmation` | string | Yes   | Confirmation of the new password                 |

**Notes:**
- The `current_password` must match the user's existing password.
- The `password` field must be at least 8 characters long.
- The `password_confirmation` must exactly match the `password` field.

---

## Request Example
```http
PUT /api/v1/auth/change-password
Authorization: Bearer {token}
Content-Type: application/json

{
  "current_password": "currentpassword123",
  "password": "newpassword123",
  "password_confirmation": "newpassword123"
}
```

---

## Response

### 200 OK
Returns a success message when the password is changed successfully.

#### Example
```json
{
  "message": "Password changed successfully."
}
```

---

### Error Responses
| Status | Description                              | Reference                                      |
|--------|------------------------------------------|------------------------------------------------|
| 401    | Unauthorized (not authenticated)         | [Authentication error](../_globals/authentication-errors.md) |
| 422    | Validation error (invalid input)         | See below                                      |

#### 422 Validation Error Examples
```json
{
  "message": "The current password field is required.",
  "errors": {
    "current_password": ["The current password field is required."]
  }
}
```

```json
{
  "message": "The password is incorrect.",
  "errors": {
    "current_password": ["The password is incorrect."]
  }
}
```

```json
{
  "message": "The password field must be at least 8 characters.",
  "errors": {
    "password": ["The password field must be at least 8 characters."]
  }
}
```

```json
{
  "message": "The password confirmation field must match password.",
  "errors": {
    "password": ["The password confirmation field must match password."]
  }
}
```

---

## Related Resources
- [PUT /api/v1/auth/me](update-me.md) - Update user profile information
- [POST /api/v1/auth/login](login.md) - User login
