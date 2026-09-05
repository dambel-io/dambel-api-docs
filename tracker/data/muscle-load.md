# GET /api/v1/tracker/data/muscle-load

Training load per muscle group over a date range, for the authenticated user or for a tracker
share they have been granted.


---

## Query Parameters
| Name                | Type    | Required | Description                                                                                                      |
|---------------------|---------|----------|------------------------------------------------------------------------------------------------------------------|
| `start_date`        | date    | No       | Only workouts starting on or after this day are counted. Omit for "everything".                                   |
| `end_date`          | date    | No       | Only workouts starting on or before this day are counted. Must not precede `start_date`.                          |
| `shared_tracker_id` | integer | No       | Read another athlete's load through a share they granted you (default: your own data). A share you are not party to, and one that does not exist, both return 404 — the two are indistinguishable. |

A workout is dated by its `start`, not by `tracked_at`, matching `GET /api/v1/tracker/workouts`.

---

## How the load is calculated

Per set:

```
effective_weight = weight > 0 ? weight : the athlete's latest logged bodyweight (else 0)
set_volume       = COALESCE(rep_count, 0) × effective_weight
```

Per muscle-group credit:

```
credit = set_volume × type_factor[the group's role in that exercise]
```

`type_factors` are returned in every response so a client never has to hard-code them:

| Role        | Factor |
|-------------|--------|
| `target`    | 1.0    |
| `primary`   | 0.6    |
| `secondary` | 0.3    |

A secondary mover must not be credited the same load as the target, which is what the factors are
for. They live on `App\Repositories\Tracker\Workouts\TrackerMuscleLoadRepository::TYPE_FACTORS`, so
the response, this page and the arithmetic cannot drift apart.

### Bodyweight and unweighted sets

`weight` is nullable, and a plain reps × weight would silently drop pull-ups, dips, push-ups and
every other bodyweight movement. An unweighted set is therefore priced at the athlete's most
recently logged `tracker_weights` entry. When there is no bodyweight to substitute the set
contributes `0` volume and is counted in that group's `unweighted_set_count`, so the response says
what it could not price rather than hiding it.

**Through a share, the substitution follows `include_weight`.** A viewer who was not granted
weights gets no substitution, and those sets arrive in `unweighted_set_count` instead. This is
deliberate: one unweighted set's `volume_load` divided by the `rep_count` the same viewer can
already read from `GET /api/v1/tracker/workouts` would be exactly the bodyweight the flag withheld.
A viewer's figures can therefore differ from the athlete's own for the same period.

### Replacement sets

A set logged with `is_replacement` counts, and it credits the muscles of the exercise that was
actually performed (`exercise_id`) — never those of the exercise the plan prescribed.

### The numbers are not additive

`muscle_groups` is a **flat** list. `Back` sits beside `Lats`, `Upper Back`, `Lower Back` and
`Rhomboids`, and an exercise mapped to a region *and* to a muscle inside it credits both. Summing
the groups therefore overstates the work done, and the response carries `"additive": false` to say
so.

For the same reason `normalized` is each group's share of **the largest group in the period**, never
of the sum. That still gives a 0–1 value for a colour scale or a heat map, and it does not pretend
the groups partition the work. The largest group is always exactly `1.0`; when nothing was logged,
every `normalized` is `0`.

### Caching

Results are cached for ten hours under the `tracker_muscle_load` tag, keyed on the athlete, the
share, the share's `include_weight` flag, and the window. Every write to a set — and deleting or
re-dating the parent workout — flushes the tag, so a logged set is reflected on the next request.
Writing, editing or deleting a **logged bodyweight** flushes it too, because an unweighted set is
priced at the athlete's latest bodyweight.

`include_weight` is part of the key rather than a flush trigger: it is read while the entry is
being computed, so a cached figure would otherwise stay truthful to the flag's old value for the
rest of its ten hours. Keying on it means **revoking or re-granting weight access on a share
changes this endpoint's answer on the very next request**, in both directions.

---

## Response

### 200 OK
```json
{
  "data": {
    "start_date": "2026-08-01",
    "end_date": "2026-08-31",
    "additive": false,
    "type_factors": { "target": 1.0, "primary": 0.6, "secondary": 0.3 },
    "groups": [
      {
        "muscle_group_id": 14,
        "title": "Lats",
        "translated_title": "عضلات پشتی",
        "volume_load": 48250.0,
        "normalized": 1.0,
        "set_count": 36,
        "unweighted_set_count": 4
      },
      {
        "muscle_group_id": 20,
        "title": "Biceps",
        "translated_title": "عضله دوسر بازو",
        "volume_load": 19300.0,
        "normalized": 0.4,
        "set_count": 18,
        "unweighted_set_count": 0
      }
    ]
  }
}
```

| Field                          | Type          | Description                                                                                     |
|--------------------------------|---------------|-------------------------------------------------------------------------------------------------|
| `start_date`                   | string\|null  | The window actually used: the requested range narrowed by the share's own range. `null` = unbounded. |
| `end_date`                     | string\|null  | As above, for the upper bound.                                                                    |
| `additive`                     | boolean       | Always `false`. The per-group figures overlap and must not be summed.                            |
| `type_factors`                 | object        | The weighting applied per role, so the client need not hard-code it.                              |
| `groups[].muscle_group_id`     | integer       | `muscle_groups.id`.                                                                               |
| `groups[].title`               | string        | The catalog title, in English.                                                                    |
| `groups[].translated_title`    | string        | The title in the request's `Accept-Language` locale.                                              |
| `groups[].volume_load`         | number        | Summed credit for this group over the window, rounded to two decimals.                            |
| `groups[].normalized`          | number        | `volume_load` ÷ the largest group's `volume_load`, in `[0, 1]`.                                    |
| `groups[].set_count`           | integer       | Sets that credited this group.                                                                    |
| `groups[].unweighted_set_count`| integer       | Of those, how many carried no weight the report could price.                                      |

`groups` is ordered by `volume_load`, heaviest first.

**A period with no logged workouts returns `"groups": []` with status 200, not an error.** A share
whose `include_workout` is `false` returns a byte-identical body, so a viewer cannot tell an
excluded share from a month in which nothing was logged.

---

## Error Responses
| Status | Error Type         | Reference                                                        |
|--------|--------------------|-------------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md)   |
| 404    | Not Found          | [Not found error](../../_globals/not-found-errors.md)             |
| 422    | Validation Error   | [Validation error](../../_globals/validation-errors.md)           |

---
