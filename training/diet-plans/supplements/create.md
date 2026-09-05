# POST /api/v1/training/diet-plans/{diet-plan-id}/supplements

Prescribe a supplement on a diet plan.


---

## Permissions
| Permission                      | Description                                 |
|---------------------------------|---------------------------------------------|
| `diet_plan_supplements.create`  | Create supplements for your diet plans      |
| `diet_plans.update`             | Update your own or your trainee's diet plans|

---

## URL Parameters
| Name           | Type | Required | Description             | Example |
|----------------|------|----------|-------------------------|---------|
| `diet-plan-id` | int  | Yes      | ID of the diet plan     | 12      |

---

## Request Body Parameters
| Name               | Type   | Required | Description                                                             |
|--------------------|--------|----------|-------------------------------------------------------------------------|
| `supplement_id`    | int    | Yes      | ID of a supplement in the platform catalog (must exist)                 |
| `amount`           | int    | Yes      | How much to consume                                                     |
| `amount_unit`      | string | Yes      | Unit of the amount, e.g. `mg`, `g` (max 255)                            |
| `after_meal_index` | int    | Yes      | Index of the meal this supplement is taken after/with/before            |
| `description`      | string | No       | Optional description (max 2000)                                         |

---

## Request Example
```json
POST /api/v1/training/diet-plans/12/supplements

{
  "supplement_id": 4,
  "amount": 5,
  "amount_unit": "g",
  "after_meal_index": 2,
  "description": "Take with water."
}
```

---

## Response

### 201 Created
```json
{
  "data": { /* diet plan supplement resource */ }
}
```
- [Diet Plan Supplement Resource](diet_plan_supplement_resource.md)

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
