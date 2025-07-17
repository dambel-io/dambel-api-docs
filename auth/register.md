# POST /api/v1/auth/register

Creates a new user account and returns the user resource and an API token.


---

## Request Body Parameters
| Name         | Type    | Required | Description                                 | Example                |
|--------------|---------|----------|---------------------------------------------|------------------------|
| email        | string  | Yes      | User email address                          | "user@example.com"    |
| phone        | string  | No       | User phone number (optional)                | "+1234567890"         |
| first_name   | string  | Yes      | First name of the user                      | "John"                |
| last_name    | string  | Yes      | Last name of the user                       | "Doe"                 |
| password     | string  | Yes      | User password                               | "password123"         |
| referral_code| string  | No       | Optional referral code                      | "REF123"              |

---

## Request Example
```json
{
  "email": "user@example.com",
  "phone": "+1234567890",
  "first_name": "John",
  "last_name": "Doe",
  "password": "password123",
  "referral_code": "REF123"
}
```

---

## Response

### 201 Created
Returns the created user resource and API token.

#### Example
```json
{
  "user": { /* user resource */ },
  "token": "<the API token will be set here>"
}
```

For a full schema, see [User Resource](../users/user_resource.md).

See [How to use API token?](login.md#how-to-use-api-token)

---

### Error Responses
| Status | Description                | Example/Reference                                      |
|--------|----------------------------|--------------------------------------------------------|
| 409    | Email/phone already in use | `{ "error": "Email address/phone number is already in use" }` |
| 422    | Validation error           | [Validation error](../_globals/validation-errors.md)    |
| 429    | Too many requests          | [Rate-limit error](../_globals/rate-limit-errors.md)    |
