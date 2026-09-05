# Strength Record Claim Resource

Represents one published strength-record claim: an athlete's deliberate statement that a set they
logged is a record worth ranking.


---

## Schema
| Field                    | Type            | Description                                                                 |
|--------------------------|-----------------|-----------------------------------------------------------------------------|
| `id`                     | integer         | Claim ID                                                                    |
| `user_id`                | integer         | The claimant                                                                |
| `user`                   | object          | The claimant, as a [User Resource](../../users/user_resource.md). Present only on the leaderboard, where the ranking is about who set the record. Omitted from your own claims list. |
| `tracker_workout_set_id` | integer         | The logged set the claim attests to                                         |
| `exercise_id`            | integer         | Exercise, **snapshotted at claim time**                                     |
| `rep_count`              | integer         | Repetitions, **snapshotted at claim time**                                  |
| `weight`                 | float \| null   | Weight, **snapshotted at claim time**                                       |
| `verifications_count`    | integer         | How many peers have verified the claim                                      |
| `verified_by_me`         | boolean         | Whether the authenticated caller is one of them                             |
| `withdrawn_at`           | string \| null  | Set when the athlete withdrew the claim; `null` while it is published       |
| `claimed_at`             | string          | When the claim was first published (YYYY-MM-DD HH:MM:SS)                    |

`exercise_id`, `rep_count` and `weight` are **snapshots**, not live reads through the set. Editing
the underlying set afterwards does not change a published claim — a claim is a statement about one
performance, and peers verified the numbers as they stood. Deleting the set does remove the claim
and its verifications entirely.

Nothing else about the set is exposed: its notes, its timings and the rest of that workout stay
private to the athlete.

---

## Example
```json
{
  "id": 3,
  "user_id": 7,
  "tracker_workout_set_id": 412,
  "exercise_id": 12,
  "rep_count": 3,
  "weight": 182.5,
  "verifications_count": 54,
  "verified_by_me": false,
  "withdrawn_at": null,
  "claimed_at": "2026-09-01 10:00:00"
}
```

---
