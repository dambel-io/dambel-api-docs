# DELETE /api/v1/auth/sessions/{token}

Revokes one of the caller's own sessions. Passing the id of the session making the request is allowed and has the same effect as [`POST /api/v1/auth/logout`](logout.md).

- **Authentication:** required (`auth:sanctum`)
- **Permissions:** none — a session id that is not the caller's own is treated as missing.

---

## Path Parameters
| Name    | Type    | Required | Description                                                             |
|---------|---------|----------|-------------------------------------------------------------------------|
| `token` | integer | Yes      | Session id, from [`GET /api/v1/auth/sessions`](sessions-list.md) `data[].id` |

---

## Response

### 200 OK

```json
{
  "message": "Session revoked successfully."
}
```

The revoked token is deleted; any further request with it returns 401.

---

## Error Responses
| Status | Description                                                                | Reference                                                    |
|--------|----------------------------------------------------------------------------|--------------------------------------------------------------|
| 401    | Not authenticated                                                          | [Authentication error](../_globals/authentication-errors.md)  |
| 404    | No such session, or it belongs to another user — the two are indistinguishable | [Not found error](../_globals/not-found-errors.md)            |
