# Chat Message Resource

Represents a message in a chat, including sender, content, reply information, and timestamps.


---

## Schema
| Field             | Type    | Description                                 | Example                |
|-------------------|---------|---------------------------------------------|------------------------|
| id                | int     | Unique identifier for the message           | 123                    |
| user_id           | int     | ID of the user who sent the message         | 123                    |
| user_name         | string  | Name of the user who sent the message       | "John Doe"            |
| chat_id           | int     | ID of the chat                              | 123                    |
| content           | string  | Message content                             | "Hello!"              |
| chat_message_id   | int     | ID of the message being replied to (nullable)| 456                   |
| reply_to_content  | string  | Content of the replied-to message (nullable)| "Hi there"            |
| created_at        | string  | Creation timestamp (ISO 8601 format)        | "2020-01-01 00:00:00" |
| updated_at        | string  | Last update timestamp (ISO 8601 format)     | "2020-01-01 00:00:00" |

---

## Example
```json
{
  "id": 123,
  "user_id": 123,
  "user_name": "John Doe",
  "chat_id": 123,
  "content": "Hello!",
  "chat_message_id": 456,
  "reply_to_content": "Hi there",
  "created_at": "2020-01-01 00:00:00",
  "updated_at": "2020-01-01 00:00:00"
}
```
