# POST /api/v1/training/workout-plans/{workout-plan-id}/sessions/{session-id}/groups

Link two or more of a session's exercises into one group — a superset, tri-set, giant set or circuit —
performed back to back, one round at a time.


---

## Permissions
| Permission                        | Description                                 |
|------------------------------------|---------------------------------------------|
| `workout_plan_exercises.create`    | Create exercises for your workout plans     |
| `workout_plan_sessions.update`     | Update sessions of your workout plans       |
| `workout_plans.update`             | Update your own workout plans               |

The caller must be able to edit the session — its plan's owner, or the trainer who authored it for a trainee.
Groups have no permission of their own.

---

## Request Body Parameters
| Name             | Type   | Required | Description |
|------------------|--------|----------|-------------|
| `type`           | string | Yes      | `superset` (exactly 2 exercises), `tri_set` (3), `giant_set` (4–10) or `circuit` (2–10) |
| `rest_seconds`   | int    | No       | Rest after one full round of the group, in seconds (0–600) |
| `exercise_ids`   | int[]  | Yes      | 2–10 distinct plan-exercise IDs **of this session**, in performance order |

The order of `exercise_ids` becomes each exercise's `group_position` (1, 2, …). An exercise already in another
group is moved into this one; a group it leaves with fewer than two exercises is dissolved, and one left with a
count its type no longer fits (a tri-set down to two) is renamed for its size.

A count that does not fit `type` is a 422 on `type`. An ID that belongs to another session — of this plan or of
anyone else's — is a 404.

---

## Response

### 201 Created
```json
{
  "data": { /* workout plan exercise group resource */ }
}
```
- [Workout Plan Exercise Group Resource](workout_plan_exercise_group_resource.md)

When the caller is not the plan's owner (a trainer editing a trainee's plan), the owner receives a
workout-plan-updated notification.

---

## Error Responses
| Status | Description               | Reference                                                             |
|--------|---------------------------|-----------------------------------------------------------------------|
| 422    | Validation error          | [Validation error](../../../../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../../../../_globals/authentication-errors.md) |
| 404    | Not found                 | [Not-found error](../../../../_globals/not-found-errors.md)           |
| 403    | Forbidden (no permission) | [Permission error](../../../../_globals/permission-errors.md)         |

---
