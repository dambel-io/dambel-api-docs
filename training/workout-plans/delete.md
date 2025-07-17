# `DELETE /api/v1/training/workout-plans/{workout-plan-id}`

Delete a workout plan.


---

## Permissions
| Permission             | Description                                 |
|------------------------|---------------------------------------------|
| `workout_plans.delete` | Delete your own workout plans               |

---

## Response

### 204 No Content
No content is returned when the workout plan is deleted successfully.

---

## Error Responses
- **404 Not Found:** [Not-found error](../../_globals/not-found-errors.md)
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)

---
