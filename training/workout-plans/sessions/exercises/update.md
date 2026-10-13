# PUT /api/v1/training/workout-plans/{workout-plan-id}/sessions/{session-id}/exercises/{exercise-id}

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
| `exercise_id`  | int     | No       | ID of a catalog exercise. Setting it clears `custom_name` |
| `custom_name`  | string  | No       | Free-text movement name (max 255, trimmed). Setting it clears `exercise_id` |
| `super_set_id` | int     | No       | **Deprecated** — use the [groups](../groups/create.md) endpoints. Another exercise of this session to superset with: it joins that exercise's group (renamed for its new size unless it is a circuit), or forms a new superset with it. `null` takes this exercise out of its group. Joining a group that already holds 10 exercises is a 422 on `super_set_id` |
| `set_count`    | int     | No       | Number of sets (1–50)                       |
| `rep_count`    | int     | No       | Reps per set, or the lower bound of a range (1–500) |
| `rep_count_max`| int     | No       | Upper bound of a rep range (≥ `rep_count`, max 500); `null` clears it (refused for a pyramid) |
| `set_type`     | string  | No       | Set technique — see [Set types](create.md#set-types) |
| `drop_count`   | int     | No       | Drops after the top set (1–5). Only for `drop_set` |
| `drop_percent` | int     | No       | % of load removed per drop (5–50). Only for `drop_set` |
| `mini_set_count`| int    | No       | Mini-sets or clusters (1–6). Only for `rest_pause` / `cluster` |
| `pause_seconds`| int     | No       | Intra-set pause (5–60). Only for `rest_pause` / `cluster` |
| `tempo`        | string  | No       | Four characters, digits or `X` (e.g. `3010`); `null` clears it |
| `rest_seconds` | int     | No       | Rest after this exercise, in seconds (0–600); `null` clears it |
| `description`  | string  | No       | Description (max 2000, optional)            |

*All parameters are optional. If omitted, they will not be updated.*

A row always names exactly one of a catalog exercise or a custom name, judged against the row as it will be
after the update. So `{"custom_name": "Hip abductor"}` switches a library row to a custom one in one request,
`{"exercise_id": 12}` switches it back, sending both is a 422 naming both fields, and a request that would
leave the row with neither (`{"exercise_id": null}` on a library row) is a 422 on `custom_name`.

The set structure is judged the same way. Changing `set_type` clears the stored parameters the new type does
not use (`{"set_type": "straight"}` on a drop set nulls `drop_count` and `drop_percent`); a type sent without
its required parameter (`{"set_type": "drop_set"}` on a straight set) is a 422 on that parameter; a parameter
of another technique (`{"drop_count": 2}` on a straight set) is a 422; and raising `rep_count` above the
stored `rep_count_max` is a 422 on `rep_count_max`. The rep-range check runs only when the request sends
`rep_count` or `rep_count_max`, so a row stored before ranges existed with free text in `rep_count` stays
editable.

---

## Response

### 200 OK
```json
{
  "data": { /* workout plan exercise resource */ }
}
```
- [Workout Plan Exercise Resource](workout_plan_exercise_resource.md)

---

## Error Responses
| Status | Description               | Reference                                                             |
|--------|---------------------------|-----------------------------------------------------------------------|
| 422    | Validation error          | [Validation error](../../../../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../../../../_globals/authentication-errors.md) |
| 404    | Not found                 | [Not-found error](../../../../_globals/not-found-errors.md)           |
| 403    | Forbidden (no permission) | [Permission error](../../../../_globals/permission-errors.md)         |

---
