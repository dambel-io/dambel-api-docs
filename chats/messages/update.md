# PUT /api/v1/chats/{chat-id}/messages/{message-id}

Updates a specific message in a chat.


---

## Permissions
| Permission           | Description                |
|----------------------|---------------------------|
| `chat_messages.update` | Update your own messages  |

---

## URL Parameters
| Name       | Type | Required | Description                | Example |
|------------|------|----------|----------------------------|---------|
| chat-id    | int  | Yes      | ID of the chat             | 123     |
| message-id | int  | Yes      | ID of the message to update| 456     |

---

## Request Body Parameters
| Name    | Type   | Required | Description                | Example         |
|---------|--------|----------|----------------------------|-----------------|
| content | string | Yes      | Updated message content    | "Updated text"  |

---

## Request Example
```json
{
  "content": "Updated text"
}
```

---

## Response

### 200 OK
Returns the updated chat message resource.

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
