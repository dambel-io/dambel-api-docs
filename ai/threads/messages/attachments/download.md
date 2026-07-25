# GET /api/v1/ai/threads/{thread-id}/messages/{message-id}/attachments/{attachment-id}

Downloads an attached file's binary content. Fully authenticated — unlike `/media` downloads, there is no token-in-URL access; send the Sanctum bearer token as usual.


---

## Permissions
| Permission                | Description                |
|---------------------------|---------------------------|
| `ai_thread_messages.view` | View messages (and download their attachments) in your own thread |

---

## URL Parameters
| Name          | Type | Required | Description                | Example |
|---------------|------|----------|----------------------------|---------|
| thread-id     | int  | Yes      | ID of the thread           | 123     |
| message-id    | int  | Yes      | ID of the message          | 456     |
| attachment-id | int  | Yes      | ID of the attachment       | 5       |

---

## Response

### 200 OK
Streams the file's bytes. The `Content-Disposition` header carries the original filename:

```
Content-Disposition: attachment; filename="photo.jpg"
Content-Type: image/jpeg
```

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../../../_globals/permission-errors.md) |
| 404    | Thread, message, or attachment not found; message not in thread; attachment not on message; or file missing on disk | [Not found error](../../../../_globals/not-found-errors.md) |
