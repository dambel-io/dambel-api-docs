# Tracker Meal Resource

Represents a meal record in the tracker system.


---

## Schema
| Field              | Type    | Description                                 |
|--------------------|---------|---------------------------------------------|
| `id`               | integer | Meal record ID                              |
| `user_id`          | integer | User ID                                     |
| `tracked_at`       | string  | Datetime of the meal record (YYYY-MM-DD HH:MM:SS) |
| `diet_plan_meal_id`| integer | Diet plan meal ID (if applicable)           |
| `notes`            | string  | Notes                                       |
| `is_cheat`         | boolean | Whether the meal is a cheat meal            |
| `protein`          | integer | Protein in grams (nullable)                 |
| `carb`             | integer | Carbs in grams (nullable)                   |
| `fat`              | integer | Fat in grams (nullable)                     |
| `calories`         | integer | Calories (nullable)                         |

---

## Example
```json
{
  "id": 123,
  "user_id": 123,
  "tracked_at": "2020-01-01 00:00:00",
  "diet_plan_meal_id": 123,
  "notes": "...",
  "is_cheat": false,
  "protein": 123,
  "carb": 123,
  "fat": 123,
  "calories": 123
}
```

---
