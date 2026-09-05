# GET /api/v1/tracker/data/today

Retrieve todays data and targets.


---

## Query Parameters
| Name                | Type    | Required | Description                                                      |
|---------------------|---------|----------|------------------------------------------------------------------|
| `shared_tracker_id` | string  | No       | ID of a shared tracker record (default: your own data). A share the caller is not party to, or one that does not exist, returns 404 — the two are indistinguishable.           |

---

## Response

### 200 OK
```json
{
  "consumed_water": 1.2,
  "target_water": 3,
  "last_night_sleep": "07:34:15",
  "is_sleeping": false,
  "current_weight": 78.5,
  "done_workouts": [<TrackerWorkoutResource>],
  "current_workout": <TrackerWorkoutResource|null>,
  "planned_workout": <WorkoutPlanSessionResource>,
  "planned_supplements": [<DietPlanSupplementResource>],
  "planned_meals": [<DietPlanMealResource>],
  "consumed_meals": [<TrackerMealResource>],
  "consumed_supplements": [<TrackerSupplementResource>],
  "logged_measurements": [<TrackerMeasurementResource>],
  "logged_progress_photos": [<TrackerProgressPhotoResource>]
}
```

`logged_measurements` and `logged_progress_photos` are today's entries for the two share-gated
activity types added alongside the original eight. Each is an empty array when the share excludes
its type — `include_measurement` and `include_progress_photo` respectively — and
`include_progress_photo` is `false` on a new share unless the athlete turns it on.

- [Workout Plan Session Resource](../../training/workout-plans/sessions/workout_plan_session_resource.md)
- [Diet Plan Supplement Resource](../../training/diet-plans/supplements/diet_plan_supplement_resource.md)
- [Diet Plan Meal Resource](../../training/diet-plans/meals/diet_plan_meal_resource.md)
- [Tracker Meal Resource](../meals/tracker_meal_resource.md)
- [Tracker Supplement Resource](../supplements/tracker_supplement_resource.md)
- [Tracker Workout Resource](../workouts/tracker_workout_resource.md)
- [Tracker Measurement Resource](../measurements/tracker_measurement_resource.md)
- [Tracker Progress Photo Resource](../progress-photos/tracker_progress_photo_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |

---
