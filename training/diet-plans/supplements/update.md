# PUT /api/v1/training/diet-plans/{diet-plan-id}/supplements/{supplement-id}

Update a supplement prescribed on a diet plan.


---

## Permissions
| Permission                      | Description                                 |
|---------------------------------|---------------------------------------------|
| `diet_plan_supplements.update`  | Update supplements of your diet plans       |
| `diet_plans.update`             | Update your own or your trainee's diet plans|

---

## URL Parameters
| Name            | Type | Required | Description                                    | Example |
|-----------------|------|----------|------------------------------------------------|---------|
| `diet-plan-id`  | int  | Yes      | ID of the diet plan                            | 12      |
| `supplement-id` | int  | Yes      | ID of the prescribed supplement on that plan   | 34      |

---

## Request Body Parameters
| Name               | Type   | Required | Description                                                             |
|--------------------|--------|----------|-------------------------------------------------------------------------|
| `supplement_id`    | int    | No       | ID of a supplement in the platform catalog (must exist)                 |
| `amount`           | int    | No       | How much to consume                                                     |
| `amount_unit`      | string | No       | Unit of the amount, e.g. `mg`, `g` (max 255)                            |
| `after_meal_index` | int    | No       | Index of the meal this supplement is taken after/with/before            |
| `description`      | string | No       | Optional description (max 2000); send `null` to clear it                |

*All parameters are optional. If omitted, they are not updated.*

---

## Request Example
```json
PUT /api/v1/training/diet-plans/12/supplements/34

{
  "amount": 10,
  "amount_unit": "g"
}
```

---

## Response

### 200 OK
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
| Status | Description                                        | Reference                                                          |
|--------|----------------------------------------------------|--------------------------------------------------------------------|
| 422    | Validation error                                   | [Validation error](../../../_globals/validation-errors.md)         |
| 401    | Unauthorized                                       | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)                          | [Permission error](../../../_globals/permission-errors.md)         |
| 404    | Not found, or the supplement belongs to another plan | [Not-found error](../../../_globals/not-found-errors.md)         |

---
