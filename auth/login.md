# POST /api/v1/auth/login

Authenticates a user and returns an API token for subsequent requests.


---

## Request Body Parameters
| Name        | Type    | Required | Description                                                                 | Example                |
|-------------|---------|----------|-----------------------------------------------------------------------------|------------------------|
| phone       | string  | Yes      | User phone number                                                          | "+989123456789"    |
| password    | string  | Yes      | User password                                                               | "password123"         |
| expiration  | int     | No       | Token expiration in seconds (optional; if omitted, token never expires)      | 3600                   |
| token_name  | string  | No       | Device label for the session, max 255 characters (defaults to the `User-Agent` if not provided) | "MyAppToken"          |

---

## Request Example
```json
{
  "phone": "+989123456789",
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

## New-device notification

A successful login queues a `Users\NewDeviceLoginNotification` when the user is signing in **from a device they have not been seen on before**.

The rule, exactly: the device label is `token_name` if the request sent one, otherwise the `User-Agent` truncated to 255 characters. The device is *new* when, immediately before this login's token is created, the user holds no session whose `name` equals that label. The notification carries the label and the login time and nothing else — no phone number, no token, no IP.

Consequences of matching on the label, all accepted:

- Revoking a session and signing in again from the same device notifies again.
- An app or OS update that changes the `User-Agent` notifies.
- Two identical devices sending the same label collapse into one.
- The device that registered the account is already known at its first login, because [`POST /api/v1/auth/register`](register.md) mints a token named after the same `User-Agent`.

See [Notification Resource](../notifications/notification_resource.md) for the payload shape.

---

## How to use API token?
After logging in and receiving the token, save it on the client side (e.g., in a cookie or local storage). For every subsequent API call, pass the token as a Bearer token in the headers:

```
Authorization: Bearer {token}
```
