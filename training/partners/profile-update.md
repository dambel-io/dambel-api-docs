# PUT /api/v1/training/partners/profile

Create or update your own training-partner profile — the opt-in for partner matching.


---

## Permissions
| Permission                 | Description                    |
|----------------------------|--------------------------------|
| `training_partners.update` | Write your own partner profile |

There is no path parameter and the body carries no `user_id`: the profile written is always the
caller's own.

---

## Request Body
| Name                    | Type    | Required | Description                                                       |
|-------------------------|---------|----------|-------------------------------------------------------------------|
| `is_active`             | bool    | No       | Whether you appear in other users' matches. **Defaults to `false`** |
| `headline`              | string  | No       | Max 255 characters. Nullable                                       |
| `about`                 | string  | No       | Max 1000 characters. Nullable                                      |
| `city_id`               | int     | No       | Must exist in `cities`. Nullable                                   |
| `preferred_gym_id`      | int     | No       | Must exist in `gyms`. Nullable                                     |
| `preferred_time_of_day` | string  | No       | One of `morning`, `afternoon`, `evening`, `night`. Nullable        |
| `match_gender`          | string  | No       | One of `same`, `any`. Defaults to `same`                           |
| `major_ids`             | array   | No       | Up to 10 major ids. Replaces the declared disciplines wholesale     |

Every field is optional, and a field you omit is left as it is — including `major_ids`, which
changes the declared disciplines only when it is sent.

**Opting in is always explicit.** A first write with no `is_active` creates an *inactive* profile:
writing a profile does not make you discoverable. Setting `is_active` to `false` removes you from
every other user's matches on the very next request — the matching query filters on the column and
nothing is cached.

Everything on this profile is what you typed. Nothing here is inferred from your tracker data, your
gym subscriptions, or your check-in history.

---

## Response

### 201 Created
Returned by the write that creates the profile.

### 200 OK
Returned by every write after it — the same row, updated in place.

```json
{
  "data": <training partner profile resource>
}
```
- See [Training Partner Profile Resource](training_partner_profile_resource.md)

---

## Error Responses
| Status | Error Type          | Reference                                                       |
|--------|---------------------|-----------------------------------------------------------------|
| 401    | Unauthorized        | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden           | [Permission error](../../_globals/permission-errors.md)         |
| 422    | Validation Error    | [Validation error](../../_globals/validation-errors.md)         |

---
