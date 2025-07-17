# DELETE /api/v1/chats/{chat-id}/messages/{message-id}

Deletes a specific message from a chat.


---

## Permissions
| Permission           | Description                |
|----------------------|---------------------------|
| `chat_messages.delete` | Delete your own messages  |

---

## URL Parameters
| Name       | Type | Required | Description                | Example |
|------------|------|----------|----------------------------|---------|
| chat-id    | int  | Yes      | ID of the chat             | 123     |
| message-id | int  | Yes      | ID of the message to delete| 456     |

---

## Request Example
```
DELETE /api/v1/chats/123/messages/456
Authorization: Bearer {token}
```

---

## Response

### 204 No Content
No content is returned when the message is successfully deleted.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../../_globals/not-found-errors.md) |
