# GET /api/v1/training/partners/matches

Ranked training-partner suggestions, scored against your own declared criteria.


---

## Permissions
| Permission               | Description                           |
|--------------------------|---------------------------------------|
| `training_partners.view` | Read your partner profile and matches |

---

## Query Parameters
| Name       | Type | Required | Description                                      |
|------------|------|----------|--------------------------------------------------|
| `per_page` | int  | No       | Results per page (default 50, **capped at 100**) |
| `page`     | int  | No       | Page number for pagination                        |

---

## Who appears

Only users who have **opted in** — a profile with `is_active: true`. A user with `is_active: false`,
and a user with no profile at all, appears in no response here. Setting `is_active` to `false` on
[`PUT /profile`](profile-update.md) takes effect on the very next request; nothing is cached.

You never appear in your own results.

**Nothing in this feed is inferred.** Every signal below is a column the other user typed into
their own partner profile. This endpoint reads no tracker data, no gym subscription and no
check-in history, and it must not start to.

---

## Scoring

| Signal                                  | Weight |
|-----------------------------------------|--------|
| A shared declared Major (**per major**)  | 3      |
| The same `preferred_gym_id`              | 3      |
| The same `city_id`                       | 2      |
| The same `preferred_time_of_day`         | 1      |

Scores are computed in SQL and results are ordered by score descending, then by profile id so a
page boundary is stable. A criterion you have not set contributes nothing — if you have declared
nothing at all, every candidate scores `0` and the feed is simply the other opted-in users.

---

## Gender rules

Applied as filters, before anything is scored.

- A profile whose `match_gender` is `same` is matched only with users of the same `users.gender`.
  This is honoured **in both directions**: it narrows your own results, and it also keeps a
  candidate who asked for it out of the results of a caller with a differing gender.
- When you and a candidate both name the **same** `preferred_gym_id` and your genders differ, that
  pair is excluded unless that gym has at least one `genderless`
  [working period](../../gyms/working-periods/index.md). Only that pair at that gym is affected —
  the same candidate at a different gym, or at none, is unaffected.
- A `null` gender and a gender of `other` constrain nothing and are **never excluded** by either
  rule, in either role. `users.gender` (`male`/`female`/`other`) and a working period's `gender`
  (`men`/`women`/`genderless`) are different vocabularies and the mapping between them is lossy.

---

## Response

### 200 OK
```json
{
  "data": [
    {
      "id": 7,
      "user_id": 42,
      "user": <user resource>,
      "headline": "Powerlifting, 5am starts",
      "about": "Training for a meet in spring.",
      "city_id": 3,
      "preferred_gym_id": 12,
      "preferred_time_of_day": "morning",
      "match_gender": "same",
      "majors": [<major resource>, ...],
      "score": 9,
      "request_status": null
    }
  ],
  "links": {<pagination data>},
  "meta": {<pagination data>}
}
```
- See [User Resource](../../users/user_resource.md) · [Major Resource](../../admin/majors/major_resource.md)
- See [Pagination Data](../../_globals/pagination-data.md)

| Field            | Type          | Description                                                                 |
|------------------|---------------|-----------------------------------------------------------------------------|
| `score`          | int           | This candidate's score against your criteria                                 |
| `request_status` | string\|null  | Your existing request to this user: `pending`, `accepted`, `declined` or `null` |

`request_status` is resolved once for the whole page, so a client does not need one call per row to
render "requested".

A match becomes a conversation only after both sides agree: send a request with
[`POST /requests`](requests-create.md), and a chat opens when the addressee accepts. Note the honest
limitation — `POST /api/v1/chats` remains open to any user id platform-wide, so this consent gate
constrains *this feature's* flow, not the chat API in general.

**A caller who has written no profile gets an empty page**, not an error: matches are computed
against your own criteria, and there are none yet. Create one with
[`PUT /profile`](profile-update.md).

**A caller whose profile exists but is `is_active: false` still reads the full ranked feed.**
Opting out removes you from *other people's* results; it does not stop you browsing. The two are
separate on purpose — someone deciding whether to opt back in can see who they would be matched
with first. Only a caller with no profile row at all gets the empty page above.

---

## Error Responses
| Status | Error Type    | Reference                                                       |
|--------|---------------|-----------------------------------------------------------------|
| 401    | Unauthorized  | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden     | [Permission error](../../_globals/permission-errors.md)         |

---
