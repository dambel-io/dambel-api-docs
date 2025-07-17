# DELETE /api/v1/media/{media-id}

Deletes an attached media file from a specified element.


---

## Permissions
You must have **update** permission for the target attachable resource.

---

## URL Parameters
| Name      | Type | Required | Description                | Example |
|-----------|------|----------|----------------------------|---------|
| media-id  | int  | Yes      | ID of the media to delete  | 123     |

---

## Request Example
```
DELETE /api/v1/media/123
Authorization: Bearer {token}
```

---

## Response

### 204 No Content
No content is returned when the media is successfully deleted.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../_globals/not-found-errors.md) |
