# POST /api/v1/auth/logout

Revokes the token that authenticated the request, ending that session server-side. Every other session of the same user is left alone — use [`DELETE /api/v1/auth/sessions`](sessions-revoke-others.md) to sign out everywhere else.

- **Authentication:** required (`auth:sanctum`)

---

## Request Body Parameters
None.

---

## Response

### 200 OK

#### Example
```json
{
  "message": "Logged out successfully."
}
```

The bearer token used for this call is deleted; any further request with it returns 401.

---

### Error Responses
| Status | Description                | Example/Reference                                      |
|--------|----------------------------|--------------------------------------------------------|
| 401    | Not authenticated          | [Authentication error](../_globals/authentication-errors.md)      |
