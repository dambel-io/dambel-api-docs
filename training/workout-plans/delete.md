# DELETE /api/v1/training/workout-plans/{workout-plan-id}

Delete a workout plan.


---

## Permissions
| Permission             | Description                                 |
|------------------------|---------------------------------------------|
| `workout_plans.delete` | Delete your own workout plans               |

---

## Response

### 204 No Content
Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "Workout plan deleted successfully."
}
```

Localized from `messages.training.workout_plans.deleted_successfully` (`fa`: “پلن تمرینی با موفقیت حذف شد.”).

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 404    | Not found                 | [Not-found error](../../_globals/not-found-errors.md)           |
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |

---
