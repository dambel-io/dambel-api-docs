# Workout Plan Exercise Resource

Represents an exercise in a workout plan session.


---

## Schema
| Field                   | Type    | Description                                 |
|-------------------------|---------|---------------------------------------------|
| `id`                    | integer | Exercise ID                                 |
| `workout_plan_session_id`| integer| Associated session ID                       |
| `exercise_id`           | integer | Catalog exercise ID (`null` for a custom exercise) |
| `exercise`           | [Exercise Resource](../../../../admin/exercises/exercise_resource.md) | Exercise data (`null` for a custom exercise) |
| `custom_name`           | string  | Free-text movement name (`null` for a catalog exercise) |
| `is_custom`             | boolean | `true` when the row names a free-text movement instead of a catalog exercise |
| `super_set_id`          | integer | **Deprecated** — read `group` / `group_position`. Derived from the group: the ID of the group's first exercise for every later member; `null` for the first member and for ungrouped exercises |
| `set_count`             | string  | Number of sets                              |
| `rep_count`             | string  | Reps per set, or the lower bound of a range. Rows written before ranges existed may hold free text (e.g. `AMRAP`) |
| `rep_count_max`         | integer | Upper bound of a rep range (nullable)       |
| `set_type`              | string  | Set technique — see [Set types](create.md#set-types) |
| `drop_count`            | integer | `drop_set`: drops after the top set (nullable) |
| `drop_percent`          | integer | `drop_set`: % of load removed per drop (nullable) |
| `mini_set_count`        | integer | `rest_pause` / `cluster`: mini-sets or clusters (nullable) |
| `pause_seconds`         | integer | `rest_pause` / `cluster`: intra-set pause (nullable) |
| `tempo`                 | string  | Four characters, digits or `X` (nullable)   |
| `rest_seconds`          | integer | Rest after this exercise, in seconds (nullable) |
| `group`                 | object  | The [exercise group](../groups/workout_plan_exercise_group_resource.md) this exercise belongs to — `{id, type, rest_seconds}` — or `null` |
| `group_position`        | integer | 1-based order inside the group (nullable) |
| `description`           | string  | Description                                 |

`set_count` and `rep_count` are stored as strings and read back as strings; the create response echoes the
integers the request sent. Parse both forms.

Exactly one of `exercise_id` and `custom_name` is set. Clients should branch on `is_custom` rather than infer
it from nulls.

To log a set of a custom plan exercise in the tracker, send its `custom_name` (and this row's `id` as
`workout_plan_exercise_id`) to [create a tracker workout set](../../../../tracker/workouts/sets/create.md),
with no `exercise_id`.

---

## Example
```json
{
  "id": 123,
  "workout_plan_session_id": 123,
  "exercise_id": 123,
  "custom_name": null,
  "is_custom": false,
  "super_set_id": null,
  "set_count": "3",
  "rep_count": "8",
  "rep_count_max": 12,
  "set_type": "drop_set",
  "drop_count": 2,
  "drop_percent": 20,
  "mini_set_count": null,
  "pause_seconds": null,
  "tempo": "3010",
  "rest_seconds": 90,
  "group": { "id": 7, "type": "superset", "rest_seconds": 90 },
  "group_position": 1,
  "description": "..."
}
```

---
