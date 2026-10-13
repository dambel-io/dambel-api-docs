# GET /api/v1/training/workout-plans/{workout-plan-id}/muscle-load

The load a workout plan is *designed* to place on each muscle group — whole-plan totals **and** a
per-session breakdown — so the intended distribution can be drawn before a single set is logged.


Route name: `api.v1.training.workout-plans.muscle-load`.

---

## Permissions
| Permission           | Description                                                        |
|----------------------|--------------------------------------------------------------------|
| `workout_plans.view` | View your own workout plans, or those you authored for a trainee    |

The audience is exactly whoever may already view the plan: its owner, and the trainer of the
trainee it was authored for. **There is no tracker share involved.** This endpoint reads the plan,
never `tracker_workout_sets`, so being admitted here says nothing about access to the athlete's
*actual* logged load — that stays behind the share's `include_workout` flag on
[`GET /api/v1/tracker/data/muscle-load`](../../tracker/data/muscle-load.md).

---

## Path Parameters
| Name                 | Type    | Required | Description                                      |
|----------------------|---------|----------|--------------------------------------------------|
| `workout-plan-id`    | integer | Yes      | `workout_plans.id`. A plan you may not view returns 403. |

There are no query parameters and no request body.

---

## How the load is calculated

Per prescribed exercise, per muscle-group credit:

```
credit = set_count × effective_reps × type_factor[the group's role in that exercise]
planned_rep_load(group) = Σ credit over every prescribed exercise in scope
```

### Effective reps

`effective_reps` is what one prescribed set asks of the muscle, from the exercise's
[set structure](sessions/exercises/create.md#set-types):

| Set structure                         | `effective_reps` | Example |
|---------------------------------------|------------------|---------|
| plain `rep_count`                     | `rep_count`      | 3 × 10 → 30 |
| rep range (`rep_count_max` set), incl. `pyramid` / `reverse_pyramid` | midpoint, `(rep_count + rep_count_max) / 2` | 3 × 8–12 → 30 |
| `drop_set`                            | reps × (1 + `drop_count`) | 3 × 10, 2 drops → 90 |
| `rest_pause`                          | reps × (1 + `mini_set_count`) | 2 × 8, 2 mini-sets → 48 |
| `cluster`                             | `rep_count` (already the total per set) | 3 × 12 → 36 |
| `amrap` / `to_failure`                | `rep_count` (the reps expected) | 2 × 10 → 20 |

Each drop or mini-set is credited the reps of the top set, an approximation that errs toward the
work done. A range's midpoint may be fractional (8–11 → 9.5). `planned_set_count` stays the prescribed
sets — the drops and mini-sets live inside them. No set technique sends a row to `unparsed_exercise_count`.

`type_factors` are returned in every response so a client never has to hard-code them:

| Role        | Factor |
|-------------|--------|
| `target`    | 1.0    |
| `primary`   | 0.6    |
| `secondary` | 0.3    |

A secondary mover must not be credited the same load as the target, which is what the factors are
for. They live on `App\Repositories\Tracker\Workouts\TrackerMuscleLoadRepository::TYPE_FACTORS` —
the same constant the tracker report uses — so the response, this page and the arithmetic cannot
drift apart.

### `planned_rep_load` is not `volume_load`

`workout_plan_exercises` carries **no `weight` column**: a plan prescribes sets and reps, not load.
The tracker report's reps × effective weight therefore cannot carry over, and this endpoint's unit
is deliberately named `planned_rep_load` instead. The two figures differ by two to three orders of
magnitude and **must never be added, diffed or plotted on one axis**. The response says so on the
wire with `"unit": "planned_rep_load"` and `"comparable_to_volume_load": false`.

Only the `normalized` 0–1 *shapes* of the two endpoints may be laid over one another — that is what
lets "what the plan intends" and
[what was actually trained](../../tracker/data/muscle-load.md) be drawn on the same body map.

### Exercise groups

Supersets, tri-sets, giant sets and circuits ([exercise groups](sessions/groups/workout_plan_exercise_group_resource.md))
do not change the load: grouping says how exercises are sequenced, not how much each prescribes. Every
member is summed on its own, with no de-duplication — none is an empty container, since `set_count` and
`rep_count` are `NOT NULL` and every write path validates them `required|integer|min:1`.

### Prescribed rows this report cannot use

`set_count` and `rep_count` are `string` columns that predate the `integer|min:1` validation every
current write path applies, so a legacy `''`, `'abc'`, `'0'` or `'-3'` is possible. An exercise
counts only when both read as at least `1`, and — when it has a range — `rep_count_max` is not below
`rep_count` (no write path accepts that; only a row written directly could hold it). A row that credits no muscle group at all — its catalog
entry has no muscle-group mapping, or every mapping carries a role outside `type_factors` — cannot
be counted either. In every one of those cases the row contributes **nothing** and is *surfaced*
rather than silently dropped:

- `unparsed_exercise_count` at the top level — distinct exercise rows in the whole plan that
  contribute to no figure, whether because their counts could not be read **or** because they
  credit no muscle group;
- the same figure per session;
- per group, how many credits to that group were skipped because the counts could not be read.

A non-zero count is a client's signal that the figure beside it is short.

### The numbers are not additive

`muscle_groups` is a **flat** list. `Back` sits beside `Lats`, `Upper Back` and `Rhomboids`, and an
exercise mapped to a region *and* to a muscle inside it credits both. Summing the groups therefore
overstates the prescription, and the response carries `"additive": false` to say so.

For the same reason `normalized` is each group's share of **the largest group**, never of the sum.
The largest group is always exactly `1`; when a scope has no credits at all, every `normalized`
is `0`.

> **Number formatting.** Every numeric field is a JSON number, and a whole value is emitted without
> a fractional part — `1`, not `1.0`, and `96`, not `96.0`. A client in a strictly-typed language
> should read these as a floating-point type that accepts an integer literal (in Dart, `num` or
> `(value as num).toDouble()`, never a bare `as double`).

### Two normalization scopes

This is the one subtlety worth reading twice:

- plan-level `normalized` is against the largest group **in the plan**;
- a session's `normalized` is against the largest group **in that session**.

So a light training day's shape still reads on its own, which is the point of a per-session figure.
Cross-session comparison is served by the absolute `planned_rep_load`, which is on one scale
everywhere in the response.

Each scope is rounded independently, and the plan total is folded from the **unrounded** session
figures. The plan's `planned_rep_load` is therefore the authoritative one: summing the displayed
per-session values for a group can land up to a cent per session away from it, which is worth
knowing before building a stacked bar out of them.

### Caching

Results are cached for ten hours under the `workout_plan_muscle_load` tag, keyed on the plan ID
alone — there is no window, no share and no viewer-dependent substitution here, so every viewer of
a plan gets the same numbers. Any write that can change a prescribed exercise — creating, updating
or deleting a plan, a session or an exercise itself — flushes the tag **after** the write, so an
edit is reflected on the next request. The flush is coarse on purpose: deleting a plan or a session
cascades its exercises away without any per-row repository method running, so a narrower
invalidation would miss the case that changes the most rows.

Two writes deliberately do **not** flush, because neither can change a figure: creating a bare plan
(it has no sessions, so no prescribed exercises) and deactivating a user's plans (it writes
`is_active`, which is not an input to this report). Since the flush is tag-wide, an inert one on
either would drop every other user's cached report as well.

---

## Response

### 200 OK
```json
{
  "data": {
    "workout_plan_id": 12,
    "unit": "planned_rep_load",
    "additive": false,
    "comparable_to_volume_load": false,
    "type_factors": { "target": 1, "primary": 0.6, "secondary": 0.3 },
    "unparsed_exercise_count": 0,
    "groups": [
      {
        "muscle_group_id": 14,
        "title": "Lats",
        "translated_title": "عضلات پشتی",
        "planned_rep_load": 96,
        "planned_set_count": 8,
        "planned_rep_count": 96,
        "unparsed_exercise_count": 0,
        "normalized": 1
      },
      {
        "muscle_group_id": 20,
        "title": "Biceps",
        "translated_title": "عضله دوسر بازو",
        "planned_rep_load": 28.8,
        "planned_set_count": 4,
        "planned_rep_count": 48,
        "unparsed_exercise_count": 0,
        "normalized": 0.3
      }
    ],
    "sessions": [
      {
        "workout_plan_session_id": 31,
        "title": "Pull",
        "day": "saturday",
        "unparsed_exercise_count": 0,
        "groups": [
          {
            "muscle_group_id": 14,
            "title": "Lats",
            "translated_title": "عضلات پشتی",
            "planned_rep_load": 96,
            "planned_set_count": 8,
            "planned_rep_count": 96,
            "unparsed_exercise_count": 0,
            "normalized": 1
          }
        ]
      },
      {
        "workout_plan_session_id": 32,
        "title": "Rest day",
        "day": "sunday",
        "unparsed_exercise_count": 0,
        "groups": []
      }
    ]
  }
}
```

| Field                                   | Type         | Description                                                                                  |
|-----------------------------------------|--------------|-----------------------------------------------------------------------------------------------|
| `workout_plan_id`                       | integer      | `workout_plans.id` the report was built for.                                                   |
| `unit`                                  | string       | Always `"planned_rep_load"`. Names the unit so it cannot be mistaken for `volume_load`.        |
| `additive`                              | boolean      | Always `false`. The per-group figures overlap and must not be summed.                          |
| `comparable_to_volume_load`             | boolean      | Always `false`. Only the `normalized` shapes compare with the tracker report.                  |
| `type_factors`                          | object       | The weighting applied per role, so the client need not hard-code it.                           |
| `unparsed_exercise_count`               | integer      | Prescribed exercise rows in the whole plan whose counts could not be read.                     |
| `groups[].muscle_group_id`              | integer      | `muscle_groups.id`.                                                                            |
| `groups[].title`                        | string       | The catalog title, in English.                                                                 |
| `groups[].translated_title`             | string       | The title in the request's `Accept-Language` locale.                                           |
| `groups[].planned_rep_load`             | number       | Summed credit for this group in this scope, rounded to two decimals.                           |
| `groups[].planned_set_count`            | number       | Σ `set_count` over the exercises crediting this group, unweighted by type factor. Whole in practice; a legacy fractional count is summed as-is rather than truncated. |
| `groups[].planned_rep_count`            | number       | Σ `set_count × effective_reps` over those exercises, unweighted by type factor.                 |
| `groups[].unparsed_exercise_count`      | integer      | Credits to this group skipped because the exercise's counts could not be read.                  |
| `groups[].normalized`                   | number       | `planned_rep_load` ÷ the largest group's, **in this scope**, in `[0, 1]`.                       |
| `sessions[].workout_plan_session_id`    | integer      | `workout_plan_sessions.id`.                                                                     |
| `sessions[].title`                      | string\|null | The session's title.                                                                            |
| `sessions[].day`                        | string\|null | The session's `Weekday` value (e.g. `"saturday"`).                                               |
| `sessions[].unparsed_exercise_count`    | integer      | Exercise rows in this session whose counts could not be read.                                    |
| `sessions[].groups`                     | array        | The same group row shape, normalized against **this session's** largest group.                   |

Both `groups` arrays are ordered by `planned_rep_load` descending, ties broken by
`muscle_group_id` — matching the tracker endpoint's order. `sessions` is ordered by
`workout_plan_session_id`, so it reads in the order the sessions were authored.

**Every session appears, including one with no exercises** (`"groups": []`) — an empty training day
is information, not an omission. **A plan with no sessions returns `"groups": []` and
`"sessions": []` with status 200, not an error.**

---

## No MCP tool

This endpoint has **no equivalent on the MCP server**, and that is a deliberate deferral rather than
an oversight. Neither this report nor the pre-existing
[`GET /api/v1/tracker/data/muscle-load`](../../tracker/data/muscle-load.md) is exposed as a tool
today, so adding one here alone would leave the pair inconsistent. The tool would be a read-only
mirror of `can:view,workoutPlan` with no premium gate, in the shape of
`compareWorkoutPlanToGymEquipment`; it belongs in a change that covers both reports at once.

---

## Error Responses
| Status | Error Type   | Reference                                                       |
|--------|--------------|------------------------------------------------------------------|
| 401    | Unauthorized | [Authentication error](../../_globals/authentication-errors.md)  |
| 403    | Forbidden    | [Permission error](../../_globals/permission-errors.md)          |
| 404    | Not Found    | [Not found error](../../_globals/not-found-errors.md)            |

403 covers both a caller without `workout_plans.view` and a caller who has the permission but no
relation to the plan. 404 is a plan ID that does not exist.

---
