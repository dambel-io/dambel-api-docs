# Equipment Resource

Represents an equipment item in the system.


---

## Schema
| Field                  | Type    | Description                |
|------------------------|---------|----------------------------|
| `id`                   | integer | Equipment ID               |
| `title`                | string  | Equipment name             |
| `translated_title`      | string  | Translated equipment name  |
| `description`           | string  | Description                |
| `translated_description`| string  | Translated description     |
| `link`                  | string  | Tutorial link (nullable)   |
| `exercise_ids`          | array   | IDs of related exercises   |
| `brand_ids`             | array   | IDs of related brands      |
| `major_ids`             | array   | IDs of related majors      |
| `equipment_ids`         | array   | Related equipment IDs (reserved) |

---

## Example
```json
{
  "id": 123,
  "title": "...",
  "translated_title": "...",
  "description": "...",
  "translated_description": "...",
  "link": "...",
  "exercise_ids": [],
  "brand_ids": [],
  "major_ids": [],
  "equipment_ids": []
}
```

---
