# PUT /api/v1/training/workout-plans/{workout-plan-id}/sessions/{session-id}/groups/{group-id}

Change a group's type or rest, or replace and reorder its exercises.


---

## Permissions
| Permission                        | Description                                 |
|------------------------------------|---------------------------------------------|
| `workout_plan_exercises.update`    | Update exercises for your workout plans     |
| `workout_plan_sessions.update`     | Update sessions of your workout plans       |
| `workout_plans.update`             | Update your own workout plans               |

---

## Request Body Parameters
| Name             | Type   | Required | Description |
|------------------|--------|----------|-------------|
| `type`           | string | No       | `superset`, `tri_set`, `giant_set` or `circuit` |
| `rest_seconds`   | int    | No       | Rest after one full round (0–600); `null` clears it |
| `exercise_ids`   | int[]  | No       | The group's new members, 2–10 distinct plan-exercise IDs of this session, in performance order |

*All parameters are optional. If omitted, they will not be updated.*

`exercise_ids` **replaces** the membership: listed exercises take positions 1..n in that order, and members left
out are ungrouped (they stay in the session). Exercises moved in from another group follow the same rule as on
[create](create.md).

The type must fit the member count **after** the update — `{"type": "tri_set"}` on a two-exercise group, or three
`exercise_ids` on a superset without a new `type`, is a 422 on `type`.

---

## Response

### 200 OK
```json
{
  "data": { /* workout plan exercise group resource */ }
}
```
- [Workout Plan Exercise Group Resource](workout_plan_exercise_group_resource.md)

---

## Error Responses
| Status | Description               | Reference                                                             |
|--------|---------------------------|-----------------------------------------------------------------------|
| 422    | Validation error          | [Validation error](../../../../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../../../../_globals/authentication-errors.md) |
| 404    | Not found — also when the group is not in this session, or the session not in this plan | [Not-found error](../../../../_globals/not-found-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../../../_globals/permission-errors.md)         |

---
