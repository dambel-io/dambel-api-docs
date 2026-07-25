# AI Thread Message Attachment Resource

Represents a file attached to an AI thread message.


---

## Schema
| Field         | Type   | Description                                 | Example                |
|---------------|--------|---------------------------------------------|------------------------|
| id            | int    | Unique identifier for the attachment        | 5                      |
| message_id    | int    | ID of the message it belongs to             | 456                    |
| original_name | string | The filename as uploaded by the user        | "photo.jpg"           |
| mime_type     | string | Detected MIME type (`image/jpeg`, `image/png`, `image/webp`, `application/pdf`) | "image/jpeg" |
| size_bytes    | int    | File size in bytes                          | 84213                  |
| url           | string | Relative API path for downloading the file (authenticated) | "/api/v1/ai/threads/123/messages/456/attachments/5" |
| created_at    | string | Creation timestamp (ISO 8601 format)        | "2020-01-01 00:00:00" |

---

## Example
```json
{
  "id": 5,
  "message_id": 456,
  "original_name": "photo.jpg",
  "mime_type": "image/jpeg",
  "size_bytes": 84213,
  "url": "/api/v1/ai/threads/123/messages/456/attachments/5",
  "created_at": "2020-01-01 00:00:00"
}
```
