# GET /api/v1/tracker/data/today

Retrieve todays data and targets.


---

## Response

### 200 OK
```json
{
  "consumed_water": 1.2,
  "target_water": 3,
  "last_night_sleep": "07:34:15",
  "current_weight": 78.5,
  "planned_workout": <WorkoutPlanSessionResource>,
  "planned_supplements": [<DietPlanSupplementResource>],
  "planned_meals": [<DietPlanMealResource>],
  "consumed_meals": [<TrackerMealResource>],
  "consumed_supplements": [<TrackerSupplementResource>]
}
```

- [Workout Plan Session Resource](../../training/workout-plans/sessions/workout_plan_session_resource.md)
- [Diet Plan Supplement Resource](../../training/diet-plans/supplements/diet_plan_supplement_resource.md)
- [Diet Plan Meal Resource](../../training/diet-plans/meals/diet_plan_meal_resource.md)
- [Tracker Meal Resource](../meals/tracker_meal_resource.md)
- [Tracker Supplement Resource](../supplements/tracker_supplement_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |

---
