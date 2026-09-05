# GET /api/v1/gyms

Retrieves a list of gyms, with support for filtering by location, owner, major, and more. Results can be sorted by proximity, marketing boosts, or recency.


**No authentication required.**

---

## Permissions
| Permission      | Description                                                                 |
|-----------------|-----------------------------------------------------------------------------|
| `gyms.view_all` | View all gyms, including hidden ones (admin only). Without this permission, only gyms that are **active and have an approved license** are returned, except users can always see their own gyms in any state. Also required for the `license_status` filter and for seeing the `gym_license_*` fields and the `owner` object on gyms you do not own. |

> **Visibility:** a gym is publicly listed only while `is_active` is `true` **and** `gym_license_approved` is `true`. A gym whose license is not approved — `gym_license_approved` is `null` or `false`, **including gyms that never uploaded a document** — is hidden from everyone except its owner and admins, and it cannot sell subscriptions — see [Subscribe](subscriptions/subscribe.md). Note this is broader than the `license_status=pending` filter below, which additionally requires an uploaded document; to list every hidden gym use `license_status=pending,rejected,none`.

---

## Query Parameters
| Name      | Type   | Required | Description                                                                 | Example         |
|-----------|--------|----------|-----------------------------------------------------------------------------|-----------------|
| city_id   | int    | No       | City ID(s) to filter by (comma-separated for multiple)                      | "1,2,3"        |
| state_id  | int    | No       | State ID(s) to filter by (comma-separated for multiple)                     | "4,5"          |
| country_id| int    | No       | Country ID(s) to filter by (comma-separated for multiple)                    | "6"            |
| gym_id    | int    | No       | Specific gym ID(s) to fetch (comma-separated for multiple)                   | "10,11"        |
| user_id   | int    | No       | Owner user ID(s) to filter by (comma-separated for multiple)                 | "42"           |
| major_id  | int    | No       | Major ID(s) to filter by (comma-separated for multiple)                      | "1,2"          |
| word      | string | No       | Search gyms by text across name, address and description. Max 255 characters. Persian-normalized — see the note below. | "fitness"      |
| license_status | string | No  | Filter by license review state: `pending` (uploaded, awaiting review), `approved`, `rejected`, or `none` (no document uploaded) — comma-separated to combine. **Requires `gyms.view_all` — silently ignored for everyone else**, so the public endpoint cannot be used to probe review state. | "pending,rejected" |
| page      | int    | No       | Page number for pagination                                                   | 1               |
| lat       | float  | No       | Latitude for proximity search                                                | 35.6892         |
| lng       | float  | No       | Longitude for proximity search                                               | 51.3890         |
| radius    | float  | No       | Radius in kilometers for proximity search (default: 2,000,000, min: 10, max: 2,000,000)| 50              |

> **`word` matching.** The term and the text it is matched against are both normalized first, so a
> gym stored with an Arabic keyboard's `ي`/`ك` is found by a search typed with the Persian `ی`/`ک`
> and vice versa; the same applies to hamza-bearing alefs, teh marbuta, zero-width joiners and
> non-joiners, the tatweel, Arabic diacritics, and Persian or Arabic-Indic digits (`۲۴` and `24`
> match each other). Matching is case-insensitive and matches anywhere in the text, not only at the
> start. **`%` and `_` are literal characters** — `?word=%` returns only gyms whose text actually
> contains a percent sign, not every gym. A term that normalizes to nothing (whitespace alone) is
> treated as no filter at all.

> **`license_status` details.** Values are **case-sensitive** and are matched after trimming, so `pending, none` and `pending,none` are equivalent. A value that matches none of the four (`?license_status=typo`, `?license_status=PENDING`) returns an **empty result set**, not the unfiltered list. The four values do **not** partition the gyms: `none` is defined purely on the document's absence, so a gym that has an explicit approval *and* no document on file appears under both `approved` and `none` — do not sum the four counts and expect the table total. Their union does cover every gym.

Results are sorted by marketing boosts first, then by proximity (if `lat`/`lng` provided), otherwise by newest.

> If you specify location parameters, pagination is removed and all results within the radius are returned in one page.

---

## Response

### 200 OK
Returns a paginated list of gym resources.

#### Schema
```json
{
  "data": [
    { /* Gym Resource */ }
  ],
  "links": { /* Pagination Data */ },
  "meta": { /* Pagination Data */ }
}
```

#### Example
```json
{
  "data": [
    {
      "id": 123,
      "name": "Iron Paradise",
      "address": "123 Main St",
      "location_lat": 35.6892,
      "location_lng": 51.3890,
      "is_active": true,
      "description": "A premium gym with modern equipment.",
      "created_at": "2023-01-01 10:00:00",
      "updated_at": "2023-01-01 10:00:00",
      "show_crowd": false,
      "crowd": null,
      "city": {
        "id": 5,
        "name": "Tehran",
        "state": {
          "id": 1,
          "name": "Tehran Province"
        }
      },
      "majors": [
        { "id": 1, "title": "Bodybuilding" },
        { "id": 2, "title": "Crossfit" }
      ],
      "working_periods": [],
      "working_status": null,
      "boost": null,
      "media": [],
      "rating_count": 0,
      "rating_average": 0
    }
  ],
  "links": {
    "first": "https://api.example.com/api/v1/gyms?page=1",
    "last": "https://api.example.com/api/v1/gyms?page=10",
    "prev": null,
    "next": "https://api.example.com/api/v1/gyms?page=2"
  },
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 10,
    "path": "https://api.example.com/api/v1/gyms",
    "per_page": 30,
    "to": 30,
    "total": 300
  }
}
```

For a full schema, see [Gym Resource](gym_resource.md) and [Pagination Data](../_globals/pagination-data.md).

> **`owner`.** Each gym carries an `owner` object — the full [User Resource](../users/user_resource.md)
> for `user_id` — but only for the gym's own owner and for viewers holding `gyms.view_all`. For every
> other caller, including anonymous ones, the key is **absent from the object entirely**. The fields
> inside it are gated again by the User resource's own rule, so `phone` and `email` need
> `users.view_all` on top.

---

### Error Responses

| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../_globals/not-found-errors.md) |
| 422    | Validation error — a comma-separated filter (`city_id`, `state_id`, `country_id`, `gym_id`, `user_id`, `major_id`, `license_status`) was sent as an array (`?city_id[]=1`) or exceeded its length bound | [Validation error](../_globals/validation-errors.md) |
