# Chat Resource

Represents a chat, including its users, last message, unread count, and creation time.


---

## Schema
| Field         | Type    | Description                                 | Example                |
|---------------|---------|---------------------------------------------|------------------------|
| id            | int     | Unique identifier for the chat              | 123                    |
| users         | array   | List of user objects in the chat            | [ { ... }, ... ]        |
| last_message  | object  | Last message resource (nullable)             | { ... }                |
| unread_count  | int     | Number of unread messages                   | 0                      |
| created_at    | string  | Creation timestamp (ISO 8601 format)        | "2020-01-01 00:00:00"  |

Each user object includes all fields from the user resource, plus:
- `is_owner`: boolean
- `last_read_at`: string (ISO 8601)

---

## Example
```json
{
  "id": 123,
  "users": [
    {
      /* user resource fields */
      "is_owner": false,
      "last_read_at": "2020-01-01 00:00:00"
    }
  ],
  "last_message": { /* chat message resource */ },
  "unread_count": 0,
  "created_at": "2020-01-01 00:00:00"
}
```

For message schema, see [Chat Message Resource](messages/chat_message_resource.md).
