# DELETE /api/v1/training/diet-plans/{diet-plan-id}/meals/{meal-id}

Remove a meal from a diet plan.


---

## Permissions
| Permission                | Description                                 |
|---------------------------|---------------------------------------------|
| `diet_plan_meals.delete`  | Delete meals from your diet plans           |
| `diet_plans.update`       | Update your own or your trainee's diet plans|

---

## URL Parameters
| Name           | Type | Required | Description                              | Example |
|----------------|------|----------|------------------------------------------|---------|
| `diet-plan-id` | int  | Yes      | ID of the diet plan                      | 12      |
| `meal-id`      | int  | Yes      | ID of the meal on that plan              | 34      |

---

## Request Example
```
DELETE /api/v1/training/diet-plans/12/meals/34
```

---

## Response

### 204 No Content
Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "Meal deleted successfully."
}
```

Localized from `messages.training.diet_plans.meals.deleted_successfully` (`fa`: “وعده غذایی با موفقیت حذف شد.”).

> When the caller is not the plan's owner (a trainer editing a trainee's plan), the owner receives a
> `DietPlanUpdatedNotification`.

---

## Error Responses
| Status | Description                                  | Reference                                                          |
|--------|----------------------------------------------|--------------------------------------------------------------------|
| 401    | Unauthorized                                 | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)                    | [Permission error](../../../_globals/permission-errors.md)         |
| 404    | Not found, or the meal belongs to another plan | [Not-found error](../../../_globals/not-found-errors.md)         |

---
