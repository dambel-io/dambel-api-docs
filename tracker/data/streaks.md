# GET /api/v1/tracker/data/streaks

Consecutive-day logging streaks and the milestone badges they have earned, per tracker type, for the
authenticated user or for a tracker share they have been granted.


---

## Query Parameters
| Name                | Type    | Required | Description                                                                                                       |
|---------------------|---------|----------|---------------------------------------------------------------------------------------------------------------------|
| `timezone`          | string  | No       | An IANA timezone name (`Asia/Tehran`, `UTC`, …) deciding where a day begins and ends. Defaults to the app's configured zone. An unknown name is a 422. |
| `shared_tracker_id` | integer | No       | Read another athlete's streaks through a share they granted you (default: your own). A share you are not party to, and one that does not exist, both return 404 — the two are indistinguishable. |

---

## What a streak is

These definitions are the feature, so they are written down rather than left to the reader.

- **A day is a calendar day in the resolved timezone.** There is no per-user timezone column, so
  the client passes its own device zone in `timezone`. When it does not, the app's configured zone
  is used, and the zone actually applied is echoed back as `timezone` in the response.
- **A streak breaks on a missed calendar day.** Today does *not* break a streak that ran through
  yesterday — the day is still in progress. `current_streak` therefore counts back from today when
  today has a log and from yesterday otherwise, and is `0` only when neither day has one.
- **Any log of that type on that day counts.** There is no threshold: two glasses of water and ten
  are both "a day with water logged". Whether a minimum should count is a product decision, not an
  implementation detail.
- **Streaks are retroactive over the athlete's whole history.** A run from last year still holds the
  record in `longest_streak`.
- **`milestones_reached` is measured against `longest_streak`, not the current one.** A milestone is
  an achievement; one earned in March does not disappear because a Tuesday was missed.

### Which types have streaks

`workout`, `meal`, `weight`, `water`, `sleep` — the value of `config('tracker.streak_types')`.
Deliberately not `wakeup` or `supplement`, which are lower-signal habits, and not workout *sets*,
which are child rows rather than a daily act.

A workout is dated by its `start`; the other four by `tracked_at`. This matches how a tracker share
dates each type.

### Reading through a share

`streaks` holds **only the types the share includes**. A type the share excludes is **absent from the
object entirely — not `0` and not `null`.** A zero would still tell the viewer the athlete is not
logging that type, which is exactly what the toggle exists to withhold.

The share's `start_date` and `end_date` also bound the window, so **a viewer's streak is not the
athlete's streak**: a share opened two days ago cannot show a streak longer than two days. Clients
should not present a shared figure as the athlete's personal best.

### Caching

**This endpoint is deliberately uncached**, unlike `/data/averages` and `/data/charts`. A streak that
is an hour stale across a day boundary is simply wrong. Each type costs one query returning a row per
day the athlete logged, not per log.

---

## Response

### 200 OK
```json
{
  "data": {
    "timezone": "Asia/Tehran",
    "streaks": {
      "workout": {
        "current_streak": 4,
        "longest_streak": 21,
        "last_logged_on": "2026-09-04",
        "milestones_reached": [3, 7, 14]
      },
      "meal": {
        "current_streak": 0,
        "longest_streak": 9,
        "last_logged_on": "2026-08-20",
        "milestones_reached": [3, 7]
      }
    },
    "milestones": [3, 7, 14, 30, 60, 100, 365]
  }
}
```

| Field                          | Type         | Description                                                                                  |
|--------------------------------|--------------|-----------------------------------------------------------------------------------------------|
| `timezone`                     | string       | The zone the day boundary was resolved in — the requested one, or the app default.             |
| `streaks`                      | object       | Keyed by tracker type. Only the types the caller may see appear; see above.                     |
| `streaks.*.current_streak`     | integer      | Consecutive days ending today or yesterday. `0` when the run does not reach either.             |
| `streaks.*.longest_streak`     | integer      | The best run over the whole window.                                                             |
| `streaks.*.last_logged_on`     | string\|null | The most recent day with a log, `YYYY-MM-DD` in `timezone`. `null` when nothing was logged.     |
| `streaks.*.milestones_reached` | integer[]    | Every configured milestone at or below `longest_streak`.                                        |
| `milestones`                   | integer[]    | The full configured ladder, so a client can render a new badge without a release.               |

An athlete who has logged nothing gets every type with `0`, `0`, `null`, `[]` — a well-formed body,
not an error.

---

## Error Responses
| Status | Error Type         | Reference                                                        |
|--------|--------------------|-------------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md)   |
| 404    | Not Found          | [Not found error](../../_globals/not-found-errors.md)             |
| 422    | Validation Error   | [Validation error](../../_globals/validation-errors.md)           |

---
