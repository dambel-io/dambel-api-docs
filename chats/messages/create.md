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

### 201 Created
Returns the created chat message resource.

#### Example
```json
{ /* chat message resource */ }
```

For a full schema, see [Chat Message Resource](chat_message_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 422    | Validation error           | [Validation error](../../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
