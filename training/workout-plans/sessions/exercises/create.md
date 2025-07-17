# `POST /api/v1/training/workout-plans/{workout-plan-id}/sessions/{session-id}/exercises`

Create an exercise for a workout plan session.


---

## Permissions
| Permission                        | Description                                 |
|------------------------------------|---------------------------------------------|
| `workout_plan_exercises.create`    | Create exercises for your workout plans     |
| `workout_plans.update`             | Update your own workout plans               |

---

## Request Body Parameters
| Name           | Type    | Required | Description                                 |
|----------------|---------|----------|---------------------------------------------|
| `exercise_id`  | int     | Yes      | ID of the exercise                          |
| `super_set_id` | int     | No       | Parent exercise ID for supersets            |
| `set_count`    | int     | Yes      | Number of sets                              |
| `rep_count`    | int     | Yes      | Number of reps per set                      |
| `description`  | string  | No       | Description (max 2000, optional)            |

---

## Response

### 201 Created
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
