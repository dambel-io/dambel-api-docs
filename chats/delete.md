# DELETE /api/v1/chats/{chat-id}

Deletes a specific chat.


---

## Permissions
| Permission     | Description         |
|----------------|---------------------|
| `chats.delete` | Delete your own chats |

---

## URL Parameters
| Name    | Type | Required | Description                | Example |
|---------|------|----------|----------------------------|---------|
| chat-id | int  | Yes      | ID of the chat to delete   | 123     |

---

## Request Example
```
DELETE /api/v1/chats/123
Authorization: Bearer {token}
```

---

## Response

### 204 No Content
No content is returned when the chat is successfully deleted.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../_globals/not-found-errors.md) |
