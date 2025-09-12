# Exercise Resource

Represents an exercise in the system.


---

## Schema
| Field                  | Type    | Description                |
|------------------------|---------|----------------------------|
| `id`                   | integer | Exercise ID                |
| `title`                | string  | Exercise name              |
| `translated_title`      | string  | Translated exercise name   |
| `description`           | string  | Description                |
| `translated_description`| string  | Translated description     |
| `link`                  | string  | Tutorial link (nullable)   |

---

## Example
```json
{
  "id": 123,
  "title": "...",
  "translated_title": "...",
  "description": "...",
  "translated_description": "...",
  "link": "..."
}
```

---
