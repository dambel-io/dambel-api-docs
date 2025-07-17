# `GET /api/v1/training/workout-plans/{workout-plan-id}/sessions/{session-id}/exercises`

Retrieve a list of exercises for a workout plan session.


---

## Permissions
| Permission                        | Description                                 |
|------------------------------------|---------------------------------------------|
| `workout_plan_exercises.view`      | View exercises of your workout plans        |
| `workout_plans.view`               | View your own workout plans                 |

---

## Response

### 200 OK
```
{
  "data": [<workout plan exercise resource>, ...]
}
```
- [Workout Plan Exercise Resource](workout_plan_exercise_resource.md)

---

## Error Responses
- **401 Unauthorized:** [Authentication error](../../../../_globals/authentication-errors.md)
- **404 Not Found:** [Not-found error](../../../../_globals/not-found-errors.md)
- **403 Forbidden:** [Permission error](../../../../_globals/permission-errors.md)

---
