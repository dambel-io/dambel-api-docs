# PUT /api/v1/training/diet-plans/{diet-plan-id}/meals/{meal-id}

Update a meal on a diet plan.


---

## Permissions
| Permission                | Description                                 |
|---------------------------|---------------------------------------------|
| `diet_plan_meals.update`  | Update meals of your diet plans             |
| `diet_plans.update`       | Update your own or your trainee's diet plans|

---

## URL Parameters
| Name           | Type | Required | Description                              | Example |
|----------------|------|----------|------------------------------------------|---------|
| `diet-plan-id` | int  | Yes      | ID of the diet plan                      | 12      |
| `meal-id`      | int  | Yes      | ID of the meal on that plan              | 34      |

---

## Request Body Parameters
| Name             | Type   | Required | Description                                              |
|------------------|--------|----------|----------------------------------------------------------|
| `title`          | string | No       | Title of the meal (max 255)                              |
| `ingredients`    | string | No       | Ingredients (max 2000)                                   |
| `description`    | string | No       | Optional description (max 2000); send `null` to clear it |
| `protein`        | int    | No       | Protein in grams                                         |
| `carb`           | int    | No       | Carbohydrate in grams                                    |
| `fat`            | int    | No       | Fat in grams                                             |
| `calories`       | int    | No       | Calories                                                 |
| `meal_index`     | int    | No       | Index of this option within its category (row position)  |
| `category_index` | int    | No       | Category of the meal (table position)                    |

*All parameters are optional. If omitted, they are not updated.*

---

## Request Example
```json
PUT /api/v1/training/diet-plans/12/meals/34

{
  "calories": 480,
  "fat": 6
}
```

---

## Response

### 200 OK
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
| Status | Description                                  | Reference                                                          |
|--------|----------------------------------------------|--------------------------------------------------------------------|
| 422    | Validation error                             | [Validation error](../../../_globals/validation-errors.md)         |
| 401    | Unauthorized                                 | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)                    | [Permission error](../../../_globals/permission-errors.md)         |
| 404    | Not found, or the meal belongs to another plan | [Not-found error](../../../_globals/not-found-errors.md)         |

---
