# POST /api/v1/chats/{chat-id}/messages

Sends a message in a specific chat.


---

## Permissions
| Permission           | Description                |
|----------------------|---------------------------|
| `chat_messages.create` | Send a message in a chat  |

---

## URL Parameters
| Name    | Type | Required | Description                | Example |
|---------|------|----------|----------------------------|---------|
| chat-id | int  | Yes      | ID of the chat             | 123     |

---

## Request Body Parameters
| Name           | Type   | Required | Description                | Example         |
|----------------|--------|----------|----------------------------|-----------------|
| content        | string | Yes      | Message content            | "Hello!"        |
| chat_message_id| int    | No       | ID of the message being replied to (optional) | 456 |

---

## Request Example
```json
{
  "content": "Hello!",
  "chat_message_id": 456
}
```

---

## Response

### 200 OK
Returns the created chat message resource.

#### Example
```json
{
  "data": { /* chat message resource */ }
}
```

For a full schema, see [Chat Message Resource](chat_message_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 422    | Validation error           | [Validation error](../../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | `chat_message_id` names a message that is not in this chat | [Not found](../../_globals/not-found-errors.md) |

> **Replying across chats is refused.** `chat_message_id` is validated with `exists:`, which only
> proves the message exists somewhere on the platform. If it belongs to a different chat the
> request returns `404` rather than `403` — a `403` would confirm that the other chat's message
> exists to someone who should not be able to tell.
