# `PUT /api/v1/tracker/meals/{tracker-meal-id}`
You can update a meal record in the tracker system using this API.


## Permissions

- `tracker_meals.update`: updating tracker meal

## Params

- `tracked_at`: The datetime for the meal
- `diet_plan_meal_id`: Id of the diet plan meal if it is based on a diet plan
- `notes`: An optional notes
- `is_cheat`: A boolean to specify if the meal is a cheat meal (default is false)
- `protein`: Protein in grams (nullable)
- `carb`: Carbs in grams (nullable)
- `fat`: Fat in grams (nullable)
- `calories`: Calories (nullable)

> Are parameters are optional. If you don't pass them, they remain as they are.

## Response

### 200 OK
```json
<tracker meal resource>
```

[Tracker Meal Resource](tracker_meal_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
