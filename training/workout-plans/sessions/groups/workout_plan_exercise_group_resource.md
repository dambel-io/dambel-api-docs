# Workout Plan Exercise Group Resource

Two or more exercises of one session performed back to back, one round at a time.


---

## Schema
| Field                     | Type    | Description |
|---------------------------|---------|-------------|
| `id`                      | integer | Group ID |
| `workout_plan_session_id` | integer | The session the group belongs to |
| `type`                    | string  | `superset` (2 exercises), `tri_set` (3), `giant_set` (4–10) or `circuit` (2–10) |
| `rest_seconds`            | integer | Rest after one full round, in seconds (nullable) |
| `exercises`               | [Workout Plan Exercise Resource](../exercises/workout_plan_exercise_resource.md)[] | The members, in `group_position` order |

Groups are read through the exercises they contain — every
[plan exercise](../exercises/workout_plan_exercise_resource.md) carries its `group` and `group_position` — so
there is no endpoint that lists groups.

---

## Example
```json
{
  "id": 7,
  "workout_plan_session_id": 3,
  "type": "superset",
  "rest_seconds": 90,
  "exercises": [
    { "id": 21, "group": { "id": 7, "type": "superset", "rest_seconds": 90 }, "group_position": 1, "super_set_id": null, "...": "..." },
    { "id": 22, "group": { "id": 7, "type": "superset", "rest_seconds": 90 }, "group_position": 2, "super_set_id": 21, "...": "..." }
  ]
}
```

---
