# Post Resource

Represents a post entity, including its profile association, content, and draft status.


---

## Schema
| Field         | Type    | Description                                 |
|-------------- |---------|---------------------------------------------|
| id            | int     | Unique identifier for the post              |
| profile_type  | string  | Type of the profile (e.g., `App\\Models\\User`) |
| profile_id    | int     | ID of the profile the post belongs to        |
| title         | string  | Title of the post                           |
| content       | string  | Content of the post                         |
| is_draft      | bool    | Whether the post is a draft                  |

---

## Example
```json
{
  "id": 123,
  "profile_type": "App\\Models\\User",
  "profile_id": 42,
  "title": "My Workout",
  "content": "Did squats and deadlifts.",
  "is_draft": false
}
```
