# GET /api/v1/media/{media-id}

Downloads a media file by its ID.


---

## Permissions
You must have **view** permission for the target attachable resource.

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
