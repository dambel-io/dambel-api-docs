# DELETE /api/v1/tracker/workouts/{tracker-workout-id}/sets/{workout-set-id}

Delete a workout set record in the tracker system.


---

## Permissions
| Permission                      | Description                |
|----------------------------------|----------------------------|
| `tracker_workout_sets.delete`    | Delete tracker workout set |

---

## Request Body Parameters
_None._

---

## Response

### 204 No Content
Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "Workout set deleted successfully."
}
```

Localized from `messages.tracker.workouts.sets.deleted_successfully` (`fa`: “ست تمرینی با موفقیت حذف شد.”).

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../../_globals/permission-errors.md)         |

---
