# GET /api/v1/media/{media-id}

Downloads a media file by its ID.


**No authentication required.**

---

## Permissions
You must have **view** permission for the target attachable resource (except the ones that are accessible without authentication).

**Sensitive media.** A media row uploaded with a `purpose` (see [POST /api/v1/media](create.md)) is a private document and is never served publicly, regardless of what it is attached to. Access is decided per purpose, and any purpose without an explicit rule is denied:

| Purpose           | Who may download                                                  |
|-------------------|-------------------------------------------------------------------|
| `trainer_license` | The user the license belongs to, or a holder of `users.view_all`   |
| `gym_license`     | The gym's owner (`user_id`), or a holder of `gyms.view_all`        |

Anyone else — including anonymous callers — gets `403`.

---

## URL Parameters
| Name      | Type | Required | Description                | Example |
|-----------|------|----------|----------------------------|---------|
| media-id  | int  | Yes      | ID of the media to download| 123     |

---

## Request Example
```
GET /api/v1/media/123
Authorization: Bearer {token}
```

---

## Response

### 200 OK
The media file will be returned as a binary download.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../_globals/not-found-errors.md) |
