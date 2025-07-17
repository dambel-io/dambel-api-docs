# DELETE /api/v1/ai/threads/{thread-id}/messages/{message-id}

Deletes a specific message from an AI thread. Any message after the specified message will also be deleted, as messages are chained.


---

## Permissions
| Permission                  | Description                |
|-----------------------------|---------------------------|
| `ai_thread_messages.delete` | Delete your own thread messages |

---

## URL Parameters
| Name       | Type | Required | Description                | Example |
|------------|------|----------|----------------------------|---------|
| thread-id  | int  | Yes      | ID of the thread           | 123     |
| message-id | int  | Yes      | ID of the message to delete| 456     |

---

## Request Example
```
DELETE /api/v1/ai/threads/123/messages/456
Authorization: Bearer {token}
```

---

## Response

### 204 No Content
No content is returned when the message (and subsequent messages) are successfully deleted.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not found error](../../../_globals/not-found-errors.md) |
