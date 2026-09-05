# Training Partner Profile Resource

Returned by [`GET /profile`](profile-show.md) and [`PUT /profile`](profile-update.md).


```json
{
  "id": 7,
  "user_id": 42,
  "is_active": true,
  "headline": "Powerlifting, 5am starts",
  "about": "Training for a meet in spring.",
  "city_id": 3,
  "preferred_gym_id": 12,
  "preferred_time_of_day": "morning",
  "match_gender": "same",
  "majors": [<major resource>, ...],
  "created_at": "2026-09-04 12:00:00",
  "updated_at": "2026-09-04 12:00:00"
}
```

| Field                   | Type          | Description                                                     |
|-------------------------|---------------|-----------------------------------------------------------------|
| `id`                    | int           | Profile id                                                      |
| `user_id`               | int           | The owner. Always the caller on this endpoint                    |
| `is_active`             | bool          | Whether the user appears in other users' matches                 |
| `headline`              | string\|null  | Short self-description                                           |
| `about`                 | string\|null  | Longer self-description                                          |
| `city_id`               | int\|null     | User-declared city — not inferred from a gym or a subscription   |
| `preferred_gym_id`      | int\|null     | User-declared gym — not inferred from a subscription or check-in |
| `preferred_time_of_day` | string\|null  | `morning`, `afternoon`, `evening` or `night`                     |
| `match_gender`          | string        | `same` or `any`                                                  |
| `majors`                | array         | Declared disciplines. See [Major Resource](../../admin/majors/major_resource.md) |
| `created_at`            | string        | Creation timestamp                                               |
| `updated_at`            | string        | Last update timestamp                                            |

`majors` is present only where the endpoint loaded it; both profile endpoints do.

---
