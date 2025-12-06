# POST /api/v1/auth/register

Creates a new user account with SMS phone verification. The registration process requires two steps:

1. **First request** (without confirmation_code): Validates user data and sends a 6-digit verification code via SMS
2. **Second request** (with confirmation_code): Verifies the code and creates the user account


---

## Request Body Parameters
| Name         | Type    | Required | Description                                 | Example                |
|--------------|---------|----------|---------------------------------------------|------------------------|
| phone        | string  | Yes       | User phone number (optional)                | "+1234567890"         |
| email        | string  | No      | User email address                          | "user@example.com"    |
| username     | string  | Yes      | Username                                    | "johndoe"             |
| first_name   | string  | No      | First name of the user                      | "John"                |
| last_name    | string  | No      | Last name of the user                       | "Doe"                 |
| password     | string  | Yes      | User password                               | "password123"         |
| referral_code| string  | No       | Optional referral code                      | "REF123"              |
|| confirmation_code  | string | No       | 6-digit SMS verification code (required for account creation)             | "123456"               |

---

## Request Examples

### Step 1: Request Verification Code
Send user data without `confirmation_code` to receive SMS verification code.

```json
{
  "email": "user@example.com",
  "phone": "+1234567890",
  "username": "johndoe",
  "first_name": "John",
  "last_name": "Doe",
  "password": "password123",
  "referral_code": "REF123"
}
```

### Step 2: Complete Registration
Send the same data plus the 6-digit `confirmation_code` received via SMS to create the account.

```json
{
  "email": "user@example.com",
  "phone": "+1234567890",
  "username": "johndoe",
  "first_name": "John",
  "last_name": "Doe",
  "password": "password123",
  "referral_code": "REF123",
  "confirmation_code": "123456"
}
```

---

## Response

### Step 1: 200 OK (Verification Code Sent)
When `confirmation_code` is not provided, returns a success message indicating the verification code was sent.

#### Example
```json
{
  "message": "Phone verification code has been sent to your phone.",
  "phone": "+1234567890"
}
```

### Step 2: 201 Created (Account Created)
When `confirmation_code` is provided and valid, returns the created user resource and API token.

#### Example
```json
{
  "user": { /* user resource */ },
  "token": "<the API token will be set here>"
}
```

For a full schema, see [User Resource](../users/user_resource.md).

See [How to use API token?](login.md#how-to-use-api-token)

When [referral score](../users/user_resource.md#referral-score) of a user increases, they receive premium subscription as a reward. For each 5 points, they receive 7 days of premium subscription.

## How it works
1. **Step 1**: Client sends user registration data without `confirmation_code`
2. **Validation**: System validates all input parameters and checks for existing users
3. **SMS Code**: If validation passes, generates 6-digit code and sends via SMS using Kavenegar service
4. **Step 2**: Client sends same data plus the received `confirmation_code`
5. **Verification**: System verifies the code (checks validity and expiration - 10 minutes for registration)
6. **Account Creation**: If code is valid, creates user account and returns API token
7. **Cleanup**: Verification token is deleted after successful registration

## Security Notes
- Verification codes are hashed before storage
- Codes expire after 10 minutes
- Each code can only be used once
- SMS rate limiting prevents abuse
- Phone numbers must be unique across all users

---

---

### Error Responses
|| Status | Description                              | Example/Reference                                      |
||--------|------------------------------------------|--------------------------------------------------------|
|| 409    | Email/phone/username already in use      | `{ "error": "Email address/phone number/username is already in use" }` |
|| 422    | Validation error                         | [Validation error](../_globals/validation-errors.md)    |
|| 422    | Invalid or expired verification code     | See below                                              |
|| 429    | Too many requests                        | [Rate-limit error](../_globals/rate-limit-errors.md)    |
|| 500    | SMS sending failed                       | See below                                              |

#### 422 Verification Code Errors
**Invalid verification code:**
```json
{
  "message": "Invalid verification code.",
  "errors": {
    "confirmation_code": ["Invalid verification code."]
  }
}
```

**Expired verification code:**
```json
{
  "message": "Verification code has expired.",
  "errors": {
    "confirmation_code": ["Verification code has expired."]
  }
}
```

#### 500 SMS Send Failure
```json
{
  "message": "Failed to send SMS. Please try again later."
}
```
