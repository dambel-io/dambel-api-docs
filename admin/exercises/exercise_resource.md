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
| `link`                  | string  | Exercise GIF filename (nullable), served from `/storage/exercises/<link>` |
| `category`              | string  | Body-part category (nullable), e.g. `waist`, `chest`, `upper legs` |
| `equipment_ids`         | array   | IDs of related equipment   |
| `brand_ids`             | array   | IDs of related brands      |
| `major_ids`             | array   | IDs of related majors      |
| `muscle_groups`         | object  | Muscle group IDs grouped by type: `target`, `primary`, `secondary` (each an array of IDs) |
| `exercise_ids`          | array   | Related exercise IDs (reserved) |

---

## Example
```json
{
  "id": 123,
  "title": "3/4 Sit-Up",
  "translated_title": "...",
  "description": "...",
  "translated_description": "...",
  "link": "0001-2gPfomN.gif",
  "category": "waist",
  "equipment_ids": [],
  "brand_ids": [],
  "major_ids": [1, 3],
  "muscle_groups": {
    "target": [1],
    "primary": [34],
    "secondary": [17]
  },
  "exercise_ids": []
}
```

---
