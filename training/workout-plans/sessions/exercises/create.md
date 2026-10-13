# POST /api/v1/training/workout-plans/{workout-plan-id}/sessions/{session-id}/exercises

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
| `exercise_id`  | int     | One of   | ID of a catalog exercise. Required unless `custom_name` is sent; must not be sent with it |
| `custom_name`  | string  | One of   | Free-text movement name (max 255, trimmed) for an exercise not in the catalog. Required unless `exercise_id` is sent; must not be sent with it |
| `super_set_id` | int     | No       | **Deprecated** — use the [groups](../groups/create.md) endpoints. Another exercise of this session to superset with: it joins that exercise's group (renamed for its new size unless it is a circuit), or forms a new superset with it. A group already holding 10 exercises is a 422 on `super_set_id` |
| `set_count`    | int     | Yes      | Number of sets (1–50)                       |
| `rep_count`    | int     | Yes      | Reps per set, or the lower bound of a range (1–500) |
| `rep_count_max`| int     | No*      | Upper bound of a rep range (≥ `rep_count`, max 500). *Required for `pyramid` / `reverse_pyramid` |
| `set_type`     | string  | No       | Set technique — see [Set types](#set-types). Default `straight` |
| `drop_count`   | int     | No*      | Drops after the top set (1–5). *Required for `drop_set`; only for `drop_set` |
| `drop_percent` | int     | No       | % of load removed per drop (5–50). Only for `drop_set` |
| `mini_set_count`| int    | No*      | Mini-sets or clusters (1–6). *Required for `rest_pause` / `cluster`; only for those |
| `pause_seconds`| int     | No       | Intra-set pause (5–60). Only for `rest_pause` / `cluster` |
| `tempo`        | string  | No       | Four characters, digits or `X` (e.g. `3010`, `20X0`) |
| `rest_seconds` | int     | No       | Rest after this exercise, in seconds (0–600) |
| `description`  | string  | No       | Description (max 2000, optional)            |

Send **exactly one** of `exercise_id` or `custom_name`. Sending both, or neither, is a 422 naming both
fields; a `custom_name` of only whitespace counts as not sent. Prefer a catalog exercise when one exists — a
custom exercise has no muscle mapping (it is reported in the plan's `unparsed_exercise_count` on
[muscle-load](../../muscle-load.md)) and no known equipment (the gym [compare](../../../../gyms/equipment/compare.md)
endpoint skips it).

### Set types

`set_type` is one of the values below (default `straight`). Each technique accepts only its own parameters;
sending a parameter of another technique is a 422 on that parameter.

| `set_type`        | Required                | Optional        | Meaning |
|-------------------|-------------------------|-----------------|---------|
| `straight`        | —                       | —               | Every set at the same load and reps (default) |
| `drop_set`        | `drop_count`            | `drop_percent`  | After the top set, `drop_count` drops (1–5), each removing `drop_percent` % of the load (5–50) |
| `rest_pause`      | `mini_set_count`        | `pause_seconds` | After the top set, `mini_set_count` mini-sets (1–6) separated by `pause_seconds` (5–60) |
| `cluster`         | `mini_set_count`        | `pause_seconds` | Each set split into `mini_set_count` clusters (1–6) with `pause_seconds` between; `rep_count` is the total per set |
| `pyramid`         | `rep_count_max`         | —               | Reps descend from `rep_count_max` to `rep_count` as the load rises |
| `reverse_pyramid` | `rep_count_max`         | —               | Reps ascend from `rep_count` to `rep_count_max` as the load drops |
| `amrap`           | —                       | —               | As many reps as possible; `rep_count` is the reps expected |
| `to_failure`      | —                       | —               | Sets taken to failure; `rep_count` is the reps expected |

**Reps.** `rep_count` is the target, or the lower bound of a range when `rep_count_max` is sent
(`rep_count_max` ≥ `rep_count`, max 500). AMRAP and to-failure are set types, not rep strings — their `rep_count`
is what the coach expects, which is what the [muscle-load](../../muscle-load.md) report credits.
`tempo` is four characters, each a digit or `X` (explosive), for eccentric, bottom pause, concentric and top
pause (`3010`, `20X0`). `rest_seconds` (0–600) is the rest after this exercise's sets.

---

## Response

### 201 Created
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
