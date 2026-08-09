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
Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "Media deleted successfully."
}
```

Localized from `messages.media.deleted_successfully` (`fa`: “رسانه با موفقیت حذف شد.”).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../_globals/not-found-errors.md) |
