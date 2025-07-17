# GET /api/v1/chats/{chat-id}/messages

Retrieves a list of messages for a specific chat, with support for filtering and pagination.


---

## Permissions
| Permission         | Description                |
|--------------------|---------------------------|
| `chat_messages.view` | View messages in a chat   |

---

## URL Parameters
| Name    | Type | Required | Description                | Example |
|---------|------|----------|----------------------------|---------|
| chat-id | int  | Yes      | ID of the chat             | 123     |

---

## Query Parameters
| Name    | Type   | Required | Description                | Example         |
|---------|--------|----------|----------------------------|-----------------|
| search  | string | No       | Search text in messages    | "hello"        |
| user_id | string | No       | Filter by user ID(s), comma-separated | "1,2" |

---

## Request Example
```
GET /api/v1/chats/123/messages?search=hello&user_id=1,2
Authorization: Bearer {token}
```

---

## Response

### 200 OK
Returns a paginated list of chat message resources.

#### Example
```json
{
  "data": [ { /* chat message resource */ }, ... ],
  "links": { /* pagination data */ },
  "meta": { /* pagination data */ }
}
```

For a full schema, see [Chat Message Resource](chat_message_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../../_globals/not-found-errors.md) |
