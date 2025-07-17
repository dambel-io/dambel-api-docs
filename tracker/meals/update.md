# PUT /api/v1/tracker/meals/{tracker-meal-id}

Update a meal record in the tracker system.


---

## Permissions
| Permission                   | Description                      |
|------------------------------|----------------------------------|
| `tracker_meals.update`       | Update tracker meal record       |

---

## Request Body Parameters
| Name             | Type    | Required | Description                                 |
|------------------|---------|----------|---------------------------------------------|
| `tracked_at`     | string  | No       | Datetime for the meal record                |
| `diet_plan_meal_id`| int   | No       | Diet plan meal ID (if based on a diet plan) |
| `notes`          | string  | No       | Optional notes                              |
| `is_cheat`       | boolean | No       | Whether the meal is a cheat meal (default: false) |
| `protein`        | int     | No       | Protein in grams (nullable)                 |
| `carb`           | int     | No       | Carbs in grams (nullable)                   |
| `fat`            | int     | No       | Fat in grams (nullable)                     |
| `calories`       | int     | No       | Calories (nullable)                         |

*All parameters are optional. If omitted, they will not be updated. You can set them to null if desired.*

---

## Response

### 200 OK
```
<tracker meal resource>
```
- See [Tracker Meal Resource](tracker_meal_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 422    | Validation Error   | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
