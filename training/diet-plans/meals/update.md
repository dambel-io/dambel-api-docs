# `PUT /api/v1/training/diet-plans/{diet-plan-id}/meals/{meal-id}`
You can update a meal from a diet plan using this API.


## Permissions

- `diet_plan_meals.update`: to update meals for your diet plans
- `diet_plans.update`: to be able to update your own diet plans

## Params

- `title`: Title of the training service (maxlength 255)
- `ingredients`: Ingredietnts (maxlength 2000)
- `description`: An optional description for the training service (maxlength 2000)
- `protein`: Protein of the meal in integer (grams)
- `carb`: Carbs of the meal in integer (grams)
- `fat`: Fat of the meal in integer (grams)
- `calories`: Calories of the meal in integer
- `meal_index`: Index (option per row) of the meal
- `category_index`: Category (table) of the meal

## Response

### 200 OK
```json
<diet plan meal resource>
```

[Diet Plan Meal Resource](diet_plan_meal_resource.md)

### 422 Unprocessable Entity
[Validation error](../../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../../_globals/authentication-errors.md)

### 404 Not Found
[Not-found error](../../../_globals/not-found-errors.md)

### 403 Forbidden
[Permission error](../../../_globals/permission-errors.md)
