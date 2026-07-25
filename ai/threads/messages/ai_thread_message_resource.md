# AI Thread Message Resource

Represents a message in an AI thread, including content, role, state, and timestamps.


---

## Schema
| Field         | Type    | Description                                 | Example                |
|-------------- |---------|---------------------------------------------|------------------------|
| id            | int     | Unique identifier for the message           | 123                    |
| thread_id     | int     | ID of the thread                            | 123                    |
| content       | string  | Message content                             | "Hello!"              |
| role          | string  | Role of the sender (`user` or `assistant`)  | "user"                |
| updated_context | object  | **Deprecated** — always `null` for new messages (kept for released-app compatibility; old rows keep their stored values) | null |
| status        | string  | Message state: `completed`, or `pending_confirmation` when an interactive run paused on a confirmation-required tool | "completed" |
| function_calls | array\|null | The raw tool calls the assistant made in this message (assistant messages only) | [ { ... } ] |
| pending_tool_calls | array\|null | Tool calls not yet executed while the message awaits confirmation | [ { ... } ] |
| attachments   | array   | Attached files' metadata (present when loaded — always on create/list responses) | [ { ... } ] |
| created_at    | string  | Creation timestamp (ISO 8601 format)        | "2020-01-01 00:00:00" |

For the attachment item shape, see [AI Thread Message Attachment Resource](attachments/ai_thread_message_attachment_resource.md).

---

## Example
```json
{
  "id": 123,
  "thread_id": 123,
  "content": "Hello!",
  "role": "user",
  "updated_context": null,
  "status": "completed",
  "function_calls": null,
  "pending_tool_calls": null,
  "attachments": [
    {
      "id": 5,
      "message_id": 123,
      "original_name": "photo.jpg",
      "mime_type": "image/jpeg",
      "size_bytes": 84213,
      "url": "/api/v1/ai/threads/123/messages/123/attachments/5",
      "created_at": "2020-01-01 00:00:00"
    }
  ],
  "created_at": "2020-01-01 00:00:00"
}
```
