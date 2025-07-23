# Championship Resource

Represents a championship record for a user.


---

## Schema
| Field         | Type            | Description                                 |
|---------------|-----------------|---------------------------------------------|
| `id`          | integer         | Championship record ID                      |
| `user_id`     | integer         | Associated user ID                          |
| `title`       | string          | Title of the championship                   |
| `description` | string          | Description                                 |
| `date`        | string (date)   | Date of the championship                    |
| `media`       | array           | List of [Media Resource](../../media/media_resource.md) |

---

## Example
```json
{
  "id": 123,
  "user_id": 123,
  "title": "...",
  "description": "...",
  "date": "...",
  "media": [<media resource>, ...]
}
```

---

## Related Resources
- [Media Resource](../../media/media_resource.md)

---
