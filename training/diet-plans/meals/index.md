# `GET /api/v1/training/diet-plans/{diet-plan-id}/meals`
You can create a meal for a diet plan using this API.


## Permissions

- `diet_plan_meals.view`: to view meals of your diet plans
- `diet_plans.view`: to be able to view your own diet plans

## Response

### 200 OK
```json
{
    "data": [<diet plan meal resource>, ...],
}
```

[Diet Plan Meal Resource](diet_plan_meal_resource.md)

### 401 Unauthorized
[Authentication error](../../../_globals/authentication-errors.md)

### 404 Not Found
[Not-found error](../../../_globals/not-found-errors.md)

### 403 Forbidden
[Permission error](../../../_globals/permission-errors.md)
