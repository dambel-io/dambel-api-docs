# POST /api/v1/training/diet-plans/{diet-plan-id}/meals

Add a meal to a diet plan.


---

## Permissions
| Permission                | Description                                 |
|---------------------------|---------------------------------------------|
| `diet_plan_meals.create`  | Create meals for your diet plans            |
| `diet_plans.update`       | Update your own or your trainee's diet plans|

---

## URL Parameters
| Name           | Type | Required | Description             | Example |
|----------------|------|----------|-------------------------|---------|
| `diet-plan-id` | int  | Yes      | ID of the diet plan     | 12      |

---

## Request Body Parameters
| Name             | Type   | Required | Description                                              |
|------------------|--------|----------|----------------------------------------------------------|
| `title`          | string | Yes      | Title of the meal (max 255)                              |
| `ingredients`    | string | Yes      | Ingredients (max 2000)                                   |
| `description`    | string | No       | Optional description (max 2000)                          |
| `protein`        | int    | Yes      | Protein in grams                                         |
| `carb`           | int    | Yes      | Carbohydrate in grams                                    |
| `fat`            | int    | Yes      | Fat in grams                                             |
| `calories`       | int    | Yes      | Calories                                                 |
| `meal_index`     | int    | Yes      | Index of this option within its category (row position)  |
| `category_index` | int    | Yes      | Category of the meal (table position)                    |

---

## Request Example
```json
POST /api/v1/training/diet-plans/12/meals

{
  "title": "Chicken and rice",
  "ingredients": "200g chicken breast, 150g rice",
  "protein": 45,
  "carb": 60,
  "fat": 8,
  "calories": 520,
  "meal_index": 1,
  "category_index": 2
}
```

---

## Response

### 201 Created
```json
{
  "data": { /* diet plan meal resource */ }
}
```
- [Diet Plan Meal Resource](diet_plan_meal_resource.md)

> When the caller is not the plan's owner (a trainer editing a trainee's plan), the owner receives a
> `DietPlanUpdatedNotification`.

---

## Error Responses
| Status | Description               | Reference                                                          |
|--------|---------------------------|--------------------------------------------------------------------|
| 422    | Validation error          | [Validation error](../../../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../../_globals/permission-errors.md)         |
| 404    | Not found                 | [Not-found error](../../../_globals/not-found-errors.md)           |

---
