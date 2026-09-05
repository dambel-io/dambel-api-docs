# GET /api/v1/training/diet-plans/{diet-plan-id}/meals

List the meals prescribed by a diet plan, ordered by `category_index` then `meal_index`.


---

## Permissions
| Permission               | Description                                 |
|--------------------------|---------------------------------------------|
| `diet_plan_meals.view`   | View meals of your diet plans               |
| `diet_plans.view`        | View your own or your trainee's diet plans  |

---

## URL Parameters
| Name           | Type | Required | Description             | Example |
|----------------|------|----------|-------------------------|---------|
| `diet-plan-id` | int  | Yes      | ID of the diet plan     | 12      |

---

## Request Example
```
GET /api/v1/training/diet-plans/12/meals
```

---

## Response

### 200 OK
The whole set is returned — this endpoint is not paginated, because a diet plan's meals are bounded
by the plan itself.

```json
{
  "data": [<diet plan meal resource>, ...]
}
```
- [Diet Plan Meal Resource](diet_plan_meal_resource.md)

---

## Error Responses
| Status | Description               | Reference                                                          |
|--------|---------------------------|--------------------------------------------------------------------|
| 401    | Unauthorized              | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../../_globals/permission-errors.md)         |
| 404    | Not found                 | [Not-found error](../../../_globals/not-found-errors.md)           |

---
