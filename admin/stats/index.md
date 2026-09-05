# GET /api/v1/admin/stats

Retrieve platform statistics: the headline totals, the operator action queue (what still needs a decision), and
platform activity. It is the single round-trip behind the admin dashboard's queue and activity widgets.


---

## Permissions

The route is guarded by `can:viewAny,User`, which `UserPolicy::viewAny` grants to `users.view_all` **and** to
`users.view_limited`. Every field beyond the three legacy counts is then gated on the permission covering the data it
reveals, and **omitted entirely** — not zeroed — when the caller does not hold it.

| Permission         | Reveals                                                                                                                             |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| *(none beyond the route gate)* | `users_count`, `gyms_count`, `trainers_count`                                                                            |
| `users.view_all`   | `pending_trainer_licenses`, `new_users_today`, `new_users_last_7_days`, `ai_messages_today`, `workout_plans_created_today`, `tracker_workouts_today`, `active_users_today` |
| `gyms.view_all`    | `pending_gym_licenses`, `gym_checkins_today`                                                                                          |
| `payments.view_all`| `pending_withdrawals`, `pending_withdrawals_amount`, `active_premium_subscriptions`, `active_boosts`                                   |
| `reports.view_all` | `open_reports`, `spam_reports`                                                                                                        |

`super_admin` and `operator` hold all four, so a real operator sees every field; the gating is defence in depth
against a `users.view_limited` caller who passes the route gate.

---

## Response

### 200 OK

The response is **not** wrapped in `data` — every field sits at the response root, as the three legacy counts always
have. The example below is what a caller holding all four permissions receives.

```json
{
  "users_count": 123,
  "gyms_count": 45,
  "trainers_count": 67,

  "pending_trainer_licenses": 4,
  "new_users_today": 12,
  "new_users_last_7_days": 96,
  "ai_messages_today": 340,
  "workout_plans_created_today": 18,
  "tracker_workouts_today": 154,
  "active_users_today": 265,

  "pending_gym_licenses": 2,
  "gym_checkins_today": 210,

  "pending_withdrawals": 3,
  "pending_withdrawals_amount": 850000,
  "active_premium_subscriptions": 51,
  "active_boosts": 8,

  "open_reports": 7,
  "spam_reports": 2
}
```

---

## Schema

### Platform totals — always present

| Field            | Type    | Description                                              |
|------------------|---------|----------------------------------------------------------|
| `users_count`    | integer | Total number of registered users                          |
| `gyms_count`     | integer | Total number of gyms                                      |
| `trainers_count` | integer | Users publishing at least one training service            |

### Action queue

Each of these counts uses **the same predicate as the list filter the widget deep-links to**, so the number on the
widget always equals the total of the list the operator lands on.

Every field on this endpoint is an **integer count**, with the single exception of `pending_withdrawals_amount`,
which is a decimal Tooman amount.

| Field                        | Type    | Permission          | Predicate                                                              | Equals the total of                                                            |
|------------------------------|---------|---------------------|------------------------------------------------------------------------|---------------------------------------------------------------------------------|
| `pending_trainer_licenses`   | integer | `users.view_all`    | `trainer_license_image IS NOT NULL AND trainer_license_approved IS NULL`| `GET /users?trainer_license_status=pending`                                      |
| `pending_gym_licenses`       | integer | `gyms.view_all`     | `gym_license_image IS NOT NULL AND gym_license_approved IS NULL`        | `GET /gyms?license_status=pending`                                               |
| `pending_withdrawals`        | integer | `payments.view_all` | `type = withdrawal AND is_done = false AND rejected_at IS NULL`         | `GET /payments?type=withdrawal&is_done=false&is_rejected=false`                  |
| `pending_withdrawals_amount` | number  | `payments.view_all` | `SUM(amount)` over the same rows, in Tooman — the only non-integer field | —                                                                                |
| `open_reports`               | integer | `reports.view_all`  | `signed_off = false AND ai_marked_spam = false`                         | `GET /reports?signed_off=false&ai_marked_spam=false`                             |
| `spam_reports`               | integer | `reports.view_all`  | `signed_off = false AND ai_marked_spam = true`                          | `GET /reports?signed_off=false&ai_marked_spam=true`                              |

One predicate reads oddly on purpose:

- **`pending_withdrawals` excludes rejected-but-not-completed withdrawals**, because a rejected withdrawal needs no
  further operator action. The dashboard's deep-link must therefore send `is_rejected=false` alongside
  `type=withdrawal&is_done=false`, or the widget number and the list total will drift apart.

### Activity

All "today" figures are counted from midnight in the application timezone, and `new_users_last_7_days` from midnight
seven days ago — half-open ranges, so a row on a boundary instant falls in exactly one bucket.

Every field in this group is an **integer count**.

| Field                          | Type    | Permission          | Description                                                                                                  |
|--------------------------------|---------|---------------------|---------------------------------------------------------------------------------------------------------------|
| `new_users_today`              | integer | `users.view_all`    | Users registered since midnight                                                                                |
| `new_users_last_7_days`        | integer | `users.view_all`    | Users registered since midnight seven days ago                                                                 |
| `ai_messages_today`            | integer | `users.view_all`    | AI thread messages with role `user` sent today                                                                  |
| `workout_plans_created_today`  | integer | `users.view_all`    | Workout plans created today                                                                                     |
| `tracker_workouts_today`       | integer | `users.view_all`    | Tracker workouts started today                                                                                  |
| `active_users_today`           | integer | `users.view_all`    | Distinct users who started a tracker workout or sent an AI message today. There is no login timestamp in the schema, so activity is defined by those two actions. |
| `gym_checkins_today`           | integer | `gyms.view_all`     | Gym subscription check-ins recorded today                                                                       |
| `active_premium_subscriptions` | integer | `payments.view_all` | Premium subscriptions with `starts_at <= now` and `expires_at > now`                                            |
| `active_boosts`                | integer | `payments.view_all` | Marketing boosts with `starts_at <= now` and `ends_at > now`                                                     |

Money totals are deliberately **not** duplicated here — the dashboard reads them from
[`GET /payments/data/stats`](../../payments/data/stats.md).

---

## Errors

| Status | When                                                       |
|--------|------------------------------------------------------------|
| `401`  | No bearer token                                             |
| `403`  | Caller holds neither `users.view_all` nor `users.view_limited` |

---
