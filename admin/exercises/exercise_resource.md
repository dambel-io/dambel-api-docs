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
| `equipment_ids`         | array   | IDs of related equipment   |
| `brand_ids`             | array   | IDs of related brands      |
| `major_ids`             | array   | IDs of related majors      |
| `exercise_ids`          | array   | Related exercise IDs (reserved) |

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
  "equipment_ids": [],
  "brand_ids": [],
  "major_ids": [],
  "exercise_ids": []
}
```

---
