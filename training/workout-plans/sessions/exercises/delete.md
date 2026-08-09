# DELETE /api/v1/training/workout-plans/{workout-plan-id}/sessions/{session-id}/exercises/{exercise-id}

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
Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "Exercise deleted successfully."
}
```

Localized from `messages.training.workout_plans.exercises.deleted_successfully` (`fa`: “تمرین با موفقیت حذف شد.”).

---

## Error Responses
| Status | Description               | Reference                                                             |
|--------|---------------------------|-----------------------------------------------------------------------|
| 401    | Unauthorized              | [Authentication error](../../../../_globals/authentication-errors.md) |
| 404    | Not found                 | [Not-found error](../../../../_globals/not-found-errors.md)           |
| 403    | Forbidden (no permission) | [Permission error](../../../../_globals/permission-errors.md)         |

---
