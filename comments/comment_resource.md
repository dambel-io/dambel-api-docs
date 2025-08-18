# Comment Resource

Represents a comment entity, including its content, relationships, and timestamps.


---

## Schema

| Field             | Type   | Description                                             |
|-------------------|--------|---------------------------------------------------------|
| id                | int    | Unique identifier for the comment                       |
| user_id           | int    | ID of the user who created the comment                  |
| commentable_type  | string | The type of the resource being commented on             |
| commentable_id    | int    | The ID of the resource being commented on               |
| is_user_commentable_client    | boolean    | True if the commenter user is client of the commentable (e.g. subscriber of the gym)               |
| content           | string | The content of the comment                              |
| parent_comment_id | int    | ID of the parent comment (for replies), or null         |
| created_at        | string | Creation timestamp (ISO 8601 format)                    |
| updated_at        | string | Last update timestamp (ISO 8601 format)                 |

---

## Example

```json
{
  "id": 123,
  "user_id": 456,
  "commentable_type": "App\\Models\\Gyms\\Gym",
  "commentable_id": 42,
  "is_user_commentable_client": false,
  "content": "Great gym!",
  "parent_comment_id": null,
  "created_at": "2025-01-01 00:00:00",
  "updated_at": "2025-01-01 00:03:00"
}
```
