# DELETE /api/v1/auth/sessions

Revokes every session of the caller **except** the one making the request — "sign out everywhere else". The calling session stays valid.

- **Authentication:** required (`auth:sanctum`)
- **Permissions:** none — it only ever touches the calling user's own tokens.

---

## Request Body Parameters
None.

---

## Response

### 200 OK

```json
{
  "message": "Other sessions revoked successfully."
}
```

Every other token of the caller is deleted; further requests with any of them return 401. A user with only the calling session keeps it and gets the same response.

---

## Error Responses
| Status | Description       | Reference                                                    |
|--------|-------------------|--------------------------------------------------------------|
| 401    | Not authenticated | [Authentication error](../_globals/authentication-errors.md)  |
