# `DELETE /api/v1/training/workout-plans/{workout-plan-id}/sessions/{session-id}/exercises/{exercise-id}`

Delete an exercise from a workout plan session.


---

## Permissions
| Permission                        | Description                                 |
|------------------------------------|---------------------------------------------|
| `workout_plan_exercises.delete`    | Delete exercises for your workout plans     |
| `workout_plans.update`             | Update your own workout plans               |

---

## Response

### 204 No Content
No content is returned when the exercise is deleted successfully.

---

## Error Responses
- **401 Unauthorized:** [Authentication error](../../../../_globals/authentication-errors.md)
- **404 Not Found:** [Not-found error](../../../../_globals/not-found-errors.md)
- **403 Forbidden:** [Permission error](../../../../_globals/permission-errors.md)

---
