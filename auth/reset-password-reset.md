# POST /api/v1/auth/reset-password/reset

Resets the user's password using the 6-digit verification code received via SMS.


---

## Permissions
This endpoint does not require authentication. Rate limited to 5 requests per minute per IP address.

---

## Request Body Parameters
| Name               | Type   | Required | Description                                                                 | Example         |
|--------------------|--------|----------|-----------------------------------------------------------------------------|-----------------|
| phone              | string | Yes      | User phone number (must match the one used in request)                      | "+989123456789" |
| code               | string | Yes      | 6-digit verification code received via SMS                                 | "123456"        |
| password           | string | Yes      | New password (minimum 8 characters)                                        | "newpassword123"|
| password_confirmation | string | Yes   | Confirmation of the new password                                           | "newpassword123"|

---

## Request Example
```http
POST /api/v1/auth/reset-password/reset
Content-Type: application/json

{
  "phone": "+989123456789",
  "code": "123456",
  "password": "newpassword123",
  "password_confirmation": "newpassword123"
}
```

---

## Response

### 200 OK
Returns a success message when the password is reset successfully.

#### Example
```json
{
  "message": "Password has been reset successfully."
}
```

---

### Error Responses
| Status | Description                              | Reference                                      |
|--------|------------------------------------------|------------------------------------------------|
| 422    | Validation error (invalid input/code)    | See below                                      |
| 429    | Too many requests                        | [Rate-limit error](../_globals/rate-limit-errors.md) |

#### 422 Validation Error Examples

**Invalid or expired code:**
```json
{
  "message": "Invalid reset code.",
  "errors": {
    "code": ["Invalid reset code."]
  }
}
```

**Expired code:**
```json
{
  "message": "Reset code has expired.",
  "errors": {
    "code": ["Reset code has expired."]
  }
}
```

**Password validation errors:**
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

**Phone validation:**
```json
{
  "message": "The phone field is required.",
  "errors": {
    "phone": ["The phone field is required."]
  }
}
```

---

## How it works
1. Validates all input parameters
2. Checks if a reset token exists for the provided phone number
3. Verifies the token hasn't expired (24-hour limit)
4. Validates the provided code against the stored hashed code
5. Updates the user's password with the new one
6. Deletes the used reset token from the database

---

## Security Notes
- Verification codes are hashed before storage
- Codes expire after 24 hours
- Each code can only be used once
- Password confirmation is required
- Rate limiting prevents brute force attacks

---

## Related Resources
- [POST /api/v1/auth/reset-password/request](reset-password-request.md) - Request password reset code
- [POST /api/v1/auth/login](login.md) - User login
