# AI Thread Resource

Represents an AI thread, including its user, title, context, and creation time.


---

## Schema
| Field        | Type    | Description                                 | Example                |
|--------------|---------|---------------------------------------------|------------------------|
| id           | int     | Unique identifier for the thread            | 123                    |
| user_id      | int     | ID of the user who owns the thread          | 123                    |
| title        | string  | Title of the thread                         | "My Thread"           |
| created_at   | string  | Creation timestamp (ISO 8601 format)        | "2020-01-01 00:00:00"  |

---

## Example
```json
{
  "id": 123,
  "user_id": 123,
  "title": "My Thread",
  "created_at": "2020-01-01 00:00:00"
}
```
