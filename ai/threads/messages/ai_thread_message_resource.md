# AI Thread Message Resource

Represents a message in an AI thread, including content, role, state, and timestamps.


---

## Schema
| Field         | Type    | Description                                 | Example                |
|-------------- |---------|---------------------------------------------|------------------------|
| id            | int     | Unique identifier for the message           | 123                    |
| thread_id     | int     | ID of the thread                            | 123                    |
| content       | string  | Message content                             | "Hello!"              |
| role          | string  | Role of the sender (`user` or `assistant`)  | "user"                |
| updated_state | object  | Updated state data (nullable, JSON)         | { ... }                |
| created_at    | string  | Creation timestamp (ISO 8601 format)        | "2020-01-01 00:00:00" |

---

## Example
```json
{
  "id": 123,
  "thread_id": 123,
  "content": "Hello!",
  "role": "user",
  "updated_state": { "form": { "field": "value" } },
  "created_at": "2020-01-01 00:00:00"
}
```
