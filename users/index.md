# GET /api/v1/users

Retrieve a paginated list of users, with support for advanced filtering and sorting.


---

## Permissions
| Permission             | Description                                                                 |
|------------------------|-----------------------------------------------------------------------------|
| `users.view_all`       | View all users with full information                                       |
| `users.view_limited`   | View users with limited information (requires search parameter)            |

**Note:** Users with `users.view_limited` permission but not `users.view_all` must provide at least one character in the `search` parameter, or provide `user_id`, otherwise the API will return 0 results.

---

## Query Parameters
| Name           | Type     | Required | Description                                                                                 |
|----------------|----------|----------|---------------------------------------------------------------------------------------------|
| `page`         | integer  | No       | Page number for pagination                                                                  |
| `search`       | string   | No*      | Search text in user's first name, last name, username, email or phone. Max 255 characters. Persian-normalized — see the note below. **Required for limited access users** |
| `email_status` | string   | No       | Filter by email verification status: `verified` or `not_verified`                           |
| `phone_status` | string   | No       | Filter by phone verification status: `verified` or `not_verified`                           |
| `user_id`      | array    | No       | Filter by one or more specific user IDs                                                     |
| `trainer_license_status` | string | No | Filter by trainer license state: `pending` (uploaded, awaiting review), `approved`, `rejected`, or `none` (no document uploaded). **Requires `users.view_all`** — silently ignored for limited access users |
| `sort_by`      | string   | No       | Sort by: `name`, `email`, `phone`, `created_at`, `email_verified_at`, `phone_verified_at`   |
| `sort_order`   | string   | No       | Sort order: `desc` (default) or `asc`                                                       |

*Required when user has `users.view_limited` permission but not `users.view_all`

*Default sort is by `created_at` (newest first).*

> **`search` matching.** The term and the text it is matched against are both normalized first, so
> an account whose name is stored with an Arabic keyboard's `ي`/`ك` is found by a search typed with
> the Persian `ی`/`ک` and vice versa; the same applies to hamza-bearing alefs, teh marbuta,
> zero-width joiners and non-joiners, the tatweel, Arabic diacritics, and Persian or Arabic-Indic
> digits — so a phone number typed `۰۹۱۲…` finds one stored `0912…`. Matching is case-insensitive
> and matches anywhere in the text, not only at the start. **`%` and `_` are literal characters** —
> `?search=%` returns only accounts whose text actually contains a percent sign, not every account.
> A term that normalizes to nothing (whitespace, a lone zero-width non-joiner) is treated as no
> term at all, which for a `users.view_limited` viewer means the listing comes back empty.
>
> The five fields are matched as one string, so a term may span two of them in order — `"ali reza"`
> matches the account whose first name is `ali` and last name `reza`. A term over 255 characters is
> rejected with 422.

---

## Response

### 200 OK
```json
{
  "data": [
    {<user resource>},
    ...
  ],
  "links": {<pagination data>},
  "meta": {<pagination data>}
}
```

- [User Resource](user_resource.md)
- [Pagination Data](../_globals/pagination-data.md) (per page: 30)

---

## Error Responses
| Status | Description               | Reference                                                    |
|--------|---------------------------|--------------------------------------------------------------|
| 401    | Unauthorized              | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../_globals/permission-errors.md)         |
| 422    | `search` longer than 255 characters | [Validation error](../_globals/validation-errors.md)  |

---
