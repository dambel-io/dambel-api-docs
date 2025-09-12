# Supplement Resource

Represents a supplement in the system.


---

## Schema
| Field                  | Type    | Description                |
|------------------------|---------|----------------------------|
| `id`                   | integer | Supplement ID              |
| `title`                | string  | Supplement name            |
| `translated_title`      | string  | Translated supplement name |
| `description`           | string  | Description                |
| `translated_description`| string  | Translated description     |
| `link`                  | string  | Wiki link (nullable)       |

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
