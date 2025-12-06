# GET /api/v1/auth/verify-email/{user}

Verifies a user's email address using a signed URL sent via email.

- **Middleware:** `signed` (requires a valid signed URL)

---

## URL Parameters
| Name | Type | Required | Description | Example |
|------|------|----------|-------------|---------|
| user | int  | Yes      | User ID     | 123     |

---

## Request
This endpoint is typically accessed via a signed URL sent in an email verification email. The URL is generated with a temporary signature that expires after 60 minutes.

### Example URL
```
GET /api/v1/auth/verify-email/123?signature=abc123&expires=1640995200
```

---

## Response

### 200 OK
Returns a success message when email is verified.

#### Example
```json
{
  "message": "Email verified successfully"
}
```

### 200 OK (Already Verified)
Returns a message if the email is already verified.

#### Example
```json
{
  "message": "Email already verified"
}
```

---

### Error Responses
| Status | Description                | Example/Reference                                      |
|--------|----------------------------|--------------------------------------------------------|
| 403    | Invalid or expired signature | `{ "message": "Invalid signature" }`                 |
| 404    | User not found             | [Not found error](../_globals/not-found-errors.md)     |

---

## Email Verification Flow

1. **User Registration/Update**: When a user registers with an email or updates their email address, the `UserObserver` automatically sets `email_verified_at` to `null` and sends a verification email.

2. **Email Sent**: An email is sent to the user's email address containing a signed verification link that expires in 60 minutes.

3. **User Clicks Link**: User clicks the verification link in their email, which makes a GET request to this endpoint.

4. **Email Verified**: The endpoint validates the signed URL, checks if the email is not already verified, and sets `email_verified_at` to the current timestamp.

5. **Success Response**: User receives a success message confirming their email is verified.

---

## Security Notes

- The verification URL is signed with Laravel's URL signing mechanism
- URLs expire after 60 minutes for security
- Each verification link can only be used once (subsequent requests return "already verified")
- The endpoint does not require authentication (accessed via email link)
