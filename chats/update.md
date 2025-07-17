# PUT /api/v1/chats/{chat-id}

Updates a specific chat, such as modifying its users.


---

## Permissions
| Permission     | Description         |
|----------------|---------------------|
| `chats.update` | Update your own chat |

---

## URL Parameters
| Name    | Type | Required | Description                | Example |
|---------|------|----------|----------------------------|---------|
| chat-id | int  | Yes      | ID of the chat to update   | 123     |

---

## Request Body Parameters
| Name  | Type   | Required | Description                | Example         |
|-------|--------|----------|----------------------------|-----------------|
| users | array  | No       | Array of user IDs          | [1, 2, 3]       |

---

## Request Example
```json
{
  "users": [1, 2, 3]
}
```

---

## Response

### 200 OK
Returns the updated chat resource.

#### Example
```json
{
  "chat": { /* chat resource */ }
}
```

For a full schema, see [Chat Resource](chat_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 422    | Validation error           | [Validation error](../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
