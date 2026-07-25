# GET /api/v1/ai/threads/{thread-id}/messages/{message-id}/attachments

Lists the metadata of all files attached to a specific AI thread message.


---

## Permissions
| Permission                | Description                |
|---------------------------|---------------------------|
| `ai_thread_messages.view` | View messages (and their attachments) in your own thread |

---

## URL Parameters
| Name       | Type | Required | Description                | Example |
|------------|------|----------|----------------------------|---------|
| thread-id  | int  | Yes      | ID of the thread           | 123     |
| message-id | int  | Yes      | ID of the message          | 456     |

---

## Response

### 200 OK
Returns the message's attachments (not paginated — a message holds at most 5).

#### Example
```json
{
  "data": [
    {
      "id": 5,
      "message_id": 456,
      "original_name": "photo.jpg",
      "mime_type": "image/jpeg",
      "size_bytes": 84213,
      "url": "/api/v1/ai/threads/123/messages/456/attachments/5",
      "created_at": "2020-01-01 00:00:00"
    }
  ]
}
```

For a full schema, see [AI Thread Message Attachment Resource](ai_thread_message_attachment_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../../../_globals/permission-errors.md) |
| 404    | Thread or message not found, or message not in thread | [Not found error](../../../../_globals/not-found-errors.md) |
