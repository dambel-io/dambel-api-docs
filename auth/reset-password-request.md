# POST /api/v1/auth/reset-password/request

Initiates a password reset process by sending a 6-digit verification code via SMS to the user's phone number.


---

## Permissions
This endpoint does not require authentication. Rate limited to 5 requests per minute per IP address.

---

## Request Body Parameters
| Name    | Type   | Required | Description                                                                 | Example         |
|---------|--------|----------|-----------------------------------------------------------------------------|-----------------|
| phone   | string | Yes      | User phone number (must be registered in the system)                        | "+989123456789" |

---

## Request Example
```http
POST /api/v1/auth/reset-password/request
Content-Type: application/json

{
  "phone": "+989123456789"
}
```

---

## Response

### 200 OK
Returns a success message when the reset code SMS is sent successfully.

#### Example
```json
{
  "message": "Password reset code has been sent to your phone."
}
```

---

### Error Responses
| Status | Description                              | Reference                                      |
|--------|------------------------------------------|------------------------------------------------|
| 422    | Validation error (invalid phone number) | See below                                      |
| 429    | Too many requests                        | [Rate-limit error](../_globals/rate-limit-errors.md) |
| 500    | SMS sending failed                       | See below                                      |

#### 422 Validation Error Examples
```json
{
  "message": "The phone field is required.",
  "errors": {
    "phone": ["The phone field is required."]
  }
}
```

```json
{
  "message": "The selected phone is invalid.",
  "errors": {
    "phone": ["The selected phone is invalid."]
  }
}
```

#### 500 SMS Send Failure
```json
{
  "message": "Failed to send SMS. Please try again later."
}
```

---

## How it works
1. The system validates that the provided phone number exists in the database
2. Generates a 6-digit verification code
3. Stores the hashed code in the database with a 24-hour expiration
4. Sends the code via SMS using Kavenegar service
5. Returns success message (code is never returned in the response for security)

---

## Security Notes
- The verification code is sent only via SMS to the registered phone number
- Codes expire after 24 hours
- Failed attempts do not reveal whether a phone number exists in the system
- Rate limiting prevents abuse

---

## Related Resources
- [POST /api/v1/auth/reset-password/reset](reset-password-reset.md) - Reset password using verification code
- [POST /api/v1/auth/login](login.md) - User login
