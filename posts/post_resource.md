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
| created_at      | Datetime    | When the post is created                  |
| updated_at      | Datetime    | When the post last updated                  |
| media            | Media Resource[]    | List of media items ([see here](../media/media_resource.md))                               |

---

## Example
```json
{
  "id": 123,
  "profile_type": "App\\Models\\User",
  "profile_id": 42,
  "title": "My Workout",
  "content": "Did squats and deadlifts.",
  "is_draft": false,
  "created_at": "2020-01-01 00:00:00",
  "updated_at": "2020-03-01 00:00:00",
  "media": [
    {
      "id": 10,
      "attachable_type": "App\\Models\\Posts\\Post",
      "attachable_id": 123,
      "link": "https://example.com/media/10.jpg"
    }
  ],
}
```

## Related Resources
- [Media Resource](../media/media_resource.md)
