# GET /api/v1/auth/sessions

Lists the caller's own active sessions — one row per Sanctum token, most recently used first. Expired tokens are filtered out.

- **Authentication:** required (`auth:sanctum`)
- **Permissions:** none — the endpoint only ever reads the calling user's own tokens.

---

## Query Parameters
| Name       | Type    | Required | Description                                        |
|------------|---------|----------|----------------------------------------------------|
| `per_page` | integer | No       | Items per page, 1–100 (default: 50)                |
| `page`     | integer | No       | Page number for pagination (default: 1)            |

---

## Response

### 200 OK
Returns a paginated list of session resources, ordered by `last_used_at` descending (never-used sessions last), then `created_at` descending.

```json
{
  "data": [
    {
      "id": 42,
      "name": "Dambel/2.3.1 (Android 15; Pixel 9)",
      "current": true,
      "last_used_at": "2026-09-03 10:12:44",
      "created_at": "2026-08-30 08:00:00",
      "expires_at": null
    }
  ],
  "links": { /* pagination links */ },
  "meta": { /* pagination meta */ }
}
```

| Field          | Type           | Description                                                                                   |
|----------------|----------------|-----------------------------------------------------------------------------------------------|
| `id`           | integer        | Session id — pass it to [`DELETE /api/v1/auth/sessions/{token}`](sessions-revoke.md)          |
| `name`         | string         | The `token_name` sent at login, or the raw `User-Agent`. Client-influenced text — render escaped |
| `current`      | boolean        | True for the session making this request                                                       |
| `last_used_at` | string \| null | Last time this session made a request; null if it never has                                    |
| `created_at`   | string         | When the session was created                                                                   |
| `expires_at`   | string \| null | When the session expires; null when it does not                                                |

The token hash and abilities are never emitted.

See [Pagination](../_globals/pagination-data.md).

---

## Error Responses
| Status | Description       | Reference                                                    |
|--------|-------------------|--------------------------------------------------------------|
| 401    | Not authenticated | [Authentication error](../_globals/authentication-errors.md)  |
| 422    | Validation error  | [Validation error](../_globals/validation-errors.md)          |
