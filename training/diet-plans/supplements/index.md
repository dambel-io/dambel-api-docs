# GET /api/v1/training/diet-plans/{diet-plan-id}/supplements

List the supplements prescribed by a diet plan, ordered by `after_meal_index`.


---

## Permissions
| Permission                    | Description                                 |
|-------------------------------|---------------------------------------------|
| `diet_plan_supplements.view`  | View supplements of your diet plans         |
| `diet_plans.view`             | View your own or your trainee's diet plans  |

---

## URL Parameters
| Name           | Type | Required | Description             | Example |
|----------------|------|----------|-------------------------|---------|
| `diet-plan-id` | int  | Yes      | ID of the diet plan     | 12      |

---

## Request Example
```
GET /api/v1/training/diet-plans/12/supplements
```

---

## Response

### 200 OK
The whole set is returned — this endpoint is not paginated, because a diet plan's supplements are
bounded by the plan itself.

```json
{
  "data": [<diet plan supplement resource>, ...]
}
```
- [Diet Plan Supplement Resource](diet_plan_supplement_resource.md)

---

## Error Responses
| Status | Description               | Reference                                                          |
|--------|---------------------------|--------------------------------------------------------------------|
| 401    | Unauthorized              | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../../_globals/permission-errors.md)         |
| 404    | Not found                 | [Not-found error](../../../_globals/not-found-errors.md)           |

---
