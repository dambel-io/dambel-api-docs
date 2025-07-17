# Diet Plan Resource

Represents a diet plan.


---

## Schema
| Field         | Type    | Description                                 |
|---------------|---------|---------------------------------------------|
| `id`          | integer | Diet plan ID                                |
| `user_id`     | integer | User ID who owns the plan                   |
| `trainee_id`  | integer | Trainee ID (if applicable)                  |
| `title`       | string  | Title of the diet plan                      |
| `description` | string  | Description                                 |
| `created_at`  | string  | Creation timestamp (YYYY-MM-DD HH:MM:SS)    |
| `meals`       | array   | List of [Diet Plan Meal Resource](meals/diet_plan_meal_resource.md) |

---

## Example
```
{
  "id": 123,
  "user_id": 123,
  "trainee_id": 123,
  "title": "...",
  "description": "...",
  "created_at": "2020-01-01 00:00:00",
  "meals": [<diet plan meal resource>]
}
```

---
