# Education Resource

Represents an education record for a user.


---

## Schema
| Field         | Type            | Description                                 |
|---------------|-----------------|---------------------------------------------|
| `id`          | integer         | Education record ID                         |
| `user_id`     | integer         | Associated user ID                          |
| `school`      | string          | Name of the school                          |
| `field`       | string          | Field of education                          |
| `description` | string          | Description                                 |
| `start_date`  | string (date)   | Start date                                  |
| `end_date`    | string (date)   | End date (nullable)                         |
| `media`       | array           | List of [Media Resource](../../media/media_resource.md) |

---

## Example
```
{
  "id": 123,
  "user_id": 123,
  "school": "...",
  "field": "...",
  "description": "...",
  "start_date": "...",
  "end_date": "...",
  "media": [<media resource>, ...]
}
```

---

## Related Resources
- [Media Resource](../../media/media_resource.md)

---
