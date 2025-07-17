# `PUT /api/v1/training/workout-plans/{workout-plan-id}/sessions/{session-id}/exercises/{exercise-id}`

Update an exercise in a workout plan session.


---

## Permissions
| Permission                        | Description                                 |
|------------------------------------|---------------------------------------------|
| `workout_plan_exercises.update`    | Update exercises for your workout plans     |
| `workout_plans.update`             | Update your own workout plans               |

---

## Request Body Parameters
| Name           | Type    | Required | Description                                 |
|----------------|---------|----------|---------------------------------------------|
| `exercise_id`  | int     | No       | ID of the exercise                          |
| `super_set_id` | int     | No       | Parent exercise ID for supersets            |
| `set_count`    | int     | No       | Number of sets                              |
| `rep_count`    | int     | No       | Number of reps per set                      |
| `description`  | string  | No       | Description (max 2000, optional)            |

*All parameters are optional. If omitted, they will not be updated.*

---

## Response

### 200 OK
```
<workout plan exercise resource>
```
- [Workout Plan Exercise Resource](workout_plan_exercise_resource.md)

---

## Error Responses
- **422 Unprocessable Entity:** [Validation error](../../../../_globals/validation-errors.md)
- **401 Unauthorized:** [Authentication error](../../../../_globals/authentication-errors.md)
- **404 Not Found:** [Not-found error](../../../../_globals/not-found-errors.md)
- **403 Forbidden:** [Permission error](../../../../_globals/permission-errors.md)

---
