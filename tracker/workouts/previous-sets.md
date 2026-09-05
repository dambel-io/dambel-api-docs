# GET /api/v1/tracker/workouts/{tracker-workout-id}/previous-sets

For each exercise in a workout, return the sets the athlete logged the **last time they did that exercise**. The
workout details screen calls this once when it opens, so it can show previous weight and reps beside every exercise
without paging through the athlete's history.


---

## Permissions

| Permission                  | Description                                     |
|-----------------------------|-------------------------------------------------|
| `tracker_workouts.view`     | View the workout (and it must be the caller's)  |
| `tracker_workout_sets.view` | View tracker workout sets                        |

The workout is gated by the same `can:view,workout` policy as the rest of the `/{workout}` group, so an athlete only
ever reads their own history.

---

## Which exercises are covered

The endpoint answers for every exercise that is either

- already logged in this workout (its sets' `exercise_id`), **or**
- prescribed by the workout's linked plan session — so an exercise the athlete has not started yet still arrives with
  its history.

## Which workout counts as "previous"

For each of those exercises, in order:

1. the most recent **earlier** workout of the same athlete with the **same `workout_plan_session_id`** as the current
   workout — "what did I lift last leg day";
2. failing that, the most recent **earlier** workout of the same athlete containing that exercise at all.

`same_session` in the response says which rule produced the entry. "Earlier" is decided by the workout's `start`, not
by its id, because a workout can be back-filled after a later one was already logged. The current workout's own sets
are never returned. An exercise with no earlier history simply has no entry — the list is not padded.

---

## Query parameters

| Parameter     | Type   | Description                                                                                        |
|---------------|--------|-----------------------------------------------------------------------------------------------------|
| `exercise_id` | string | Optional comma-separated list of exercise ids to narrow the answer to. Max 30 ids; each must be a positive integer naming a real exercise. Validation errors are reported under the key `exercise_id`. |

---

## Response

### 200 OK

```json
{
  "data": [
    {
      "exercise_id": 412,
      "exercise": {<exercise resource>},
      "tracker_workout_id": 8891,
      "workout_plan_session_id": 77,
      "workout_start": "2026-08-08 10:00:00",
      "same_session": true,
      "sets": [<tracker workout set resource>, ...]
    }
  ]
}
```

The list is **not** paginated: at most **30 exercises** are answered per call, filtered or not. A plan session
holds far fewer, so the cap is a bound rather than a limit clients hit.

| Field                     | Type            | Description                                                                             |
|---------------------------|-----------------|-------------------------------------------------------------------------------------------|
| `exercise_id`             | integer         | The exercise this entry is about                                                            |
| `exercise`                | object \| null  | See [Exercise Resource](../../admin/exercises/exercise_resource.md)                         |
| `tracker_workout_id`      | integer         | The earlier workout the sets came from                                                       |
| `workout_plan_session_id` | integer \| null | That workout's plan session, if it had one                                                   |
| `workout_start`           | string          | When that workout started                                                                     |
| `same_session`            | boolean         | `true` when rule 1 applied (same plan session), `false` when it fell back to rule 2          |
| `sets`                    | array           | See [Tracker Workout Set Resource](sets/tracker_workout_set_resource.md). Oldest set first. `exercise` is omitted on these — it is already on the entry. |

---

## Error Responses

| Status | Error Type   | Reference                                                            |
|--------|--------------|-----------------------------------------------------------------------|
| 401    | Unauthorized | [Authentication error](../../_globals/authentication-errors.md)       |
| 403    | Forbidden    | [Permission error](../../_globals/permission-errors.md) — including another athlete's workout |
| 404    | Not Found    | [Not found error](../../_globals/not-found-errors.md) — no workout with that id |
| 422    | Validation   | [Validation error](../../_globals/validation-errors.md) — an unknown, non-numeric or over-cap `exercise_id`, always keyed `exercise_id` |

---
