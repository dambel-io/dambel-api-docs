# GET /api/v1/tracker/strength-records/leaderboard

A public ranking of published strength-record claims for one exercise.


---

## Permissions
_None beyond authentication._ This endpoint sits **outside** the `strength_records.view` group the
rest of this feature lives in: reading a public ranking is not the same permission as managing your
own claims, and a leaderboard nobody can read until they hold a tracker permission is not a
leaderboard.

---

## What appears here, and what never does

**Only claimed records.** Nothing an athlete logs reaches this endpoint until they publish it with
[`POST /tracker/strength-records`](create.md). The query reads `strength_record_claims`, its
verification count and the claimant — and nothing else. It never touches `tracker_workout_sets`;
the claim's `exercise_id`, `rep_count` and `weight` are snapshots taken at claim time precisely so
that it does not have to.

The consequence, which is the point of the feature: **an athlete with sets logged against this very
exercise and no claim is absent from the response entirely** — not ranked last, not anonymised,
absent. Withdrawn claims are equally absent, from the very next request.

---

## Query Parameters
| Name                | Type    | Required | Description                                                        |
|---------------------|---------|----------|--------------------------------------------------------------------|
| `exercise_id`       | int     | **Yes**  | Must exist. A leaderboard is always per-exercise                   |
| `by_rep`            | boolean | No       | Rank by `rep_count` instead of `weight`, mirroring [`/tracker/data/records`](../data/records.md) |
| `min_verifications` | int     | No       | Only claims with at least this many peer verifications (0–1000, default 0) |
| `per_page`          | int     | No       | Results per page (default 50, **clamped to 100**; a larger value is clamped, not refused) |
| `page`              | int     | No       | Page number for pagination                                          |

Ranking is by `weight` descending, then `rep_count`, then `id` — the last so a page boundary is
stable. With `by_rep=true` the first two swap.

**Unverified claims are included, with a `verifications_count` of 0.** A verified-only ranking
cannot bootstrap: a brand-new claim with no verifications would be invisible to exactly the people
who would verify it. `min_verifications` lets a client render a stricter view without a second
endpoint.

---

## Response

### 200 OK
```json
{
  "data": [<strength record claim resource>, ...],
  "links": {<pagination data>},
  "meta": {<pagination data>}
}
```
Each row carries the claimant as a nested user resource, and `verified_by_me` scoped to the
authenticated reader.

- See [Strength Record Claim Resource](strength_record_claim_resource.md)
- See [Pagination Data](../../_globals/pagination-data.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 422    | Validation Error (missing or unknown `exercise_id`) | [Validation error](../../_globals/validation-errors.md) |
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |

---
