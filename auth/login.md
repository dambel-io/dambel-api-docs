# POST /api/v1/auth/login

Authenticates a user and returns an API token for subsequent requests.


---

## Request Body Parameters
| Name        | Type    | Required | Description                                                                 | Example                |
|-------------|---------|----------|-----------------------------------------------------------------------------|------------------------|
| email       | string  | Yes      | User email address                                                          | "user@example.com"    |
| password    | string  | Yes      | User password                                                               | "password123"         |
| expiration  | int     | No       | Token expiration in seconds (optional; if omitted, token never expires)      | 3600                   |
| token_name  | string  | No       | Optional name for the token (defaults to user agent if not provided)         | "MyAppToken"          |

---

## Request Example
```json
{
  "email": "user@example.com",
  "password": "password123",
  "expiration": 3600,
  "token_name": "MyAppToken"
}
```

---

## Response

### 201 Created
Returns the API token.

#### Example
```json
{
  "token": "<the API token will be set here>"
}
```

---

### Error Responses
| Status | Description                | Example/Reference                                      |
|--------|----------------------------|--------------------------------------------------------|
| 403    | Invalid credentials        | `{ "error": "Invalid credentials" }`                 |
| 422    | Validation error           | [Validation error](../_globals/validation-errors.md)    |
| 429    | Too many requests          | [Rate-limit error](../_globals/rate-limit-errors.md)    |

---

## How to use API token?
After logging in and receiving the token, save it on the client side (e.g., in a cookie or local storage). For every subsequent API call, pass the token as a Bearer token in the headers:

```
Authorization: Bearer {token}
```
