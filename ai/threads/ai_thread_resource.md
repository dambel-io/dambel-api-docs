# AI Thread Resource

Represents an AI thread, including its user, title, context, and creation time.


---

## Schema
| Field        | Type    | Description                                 | Example                |
|--------------|---------|---------------------------------------------|------------------------|
| id           | int     | Unique identifier for the thread            | 123                    |
| user_id      | int     | ID of the user who owns the thread          | 123                    |
| title        | string  | Title of the thread                         | "My Thread"           |
| context_type  | string  | Type of the context (e.g., `App\\Models\\Plan`) | "App\\Models\\Plan"      |
| context_id    | int     | ID of the context                            | 42                     |
| created_at   | string  | Creation timestamp (ISO 8601 format)        | "2020-01-01 00:00:00"  |

---

## Example
```json
{
  "id": 123,
  "user_id": 123,
  "title": "My Thread",
  "context_type": "App\\Models\\Plan",
  "context_id": 42,
  "created_at": "2020-01-01 00:00:00"
}
```
