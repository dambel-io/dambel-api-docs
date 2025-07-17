# Media Resource

Represents a media file attached to a resource, including its type, association, and download link.


---

## Schema
| Field           | Type    | Description                                      | Example                |
|-----------------|---------|--------------------------------------------------|------------------------|
| id              | int     | Unique identifier for the media                   | 123                    |
| attachable_type | string  | Type of the attached resource (e.g., `App\\Models\\Gym`) | "App\\Models\\Gym"      |
| attachable_id   | int     | ID of the attached resource                       | 42                     |
| link            | string  | Download link for the media file                  | "https://.../file.jpg" |

---

## Example
```json
{
  "id": 123,
  "attachable_type": "App\\Models\\Gym",
  "attachable_id": 42,
  "link": "https://example.com/media/file.jpg"
}
```
