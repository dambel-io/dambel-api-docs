# GET /api/v1/training/services

Retrieve a list of training services.


**No authentication required.** A token is honoured when present (optional auth), which is what lets trainers see their own unlisted services and admins see every service.

---

## Permissions
| Permission                   | Description                                                                                              |
|------------------------------|----------------------------------------------------------------------------------------------------------|
| `training_services.view_all` | List every service, including those whose trainer's license is not approved (admin only).                |

> **Visibility:** a service is publicly listed only while its trainer's `trainer_license_approved` is `true`. Services belonging to a trainer whose license is pending (`null`) or rejected (`false`) are hidden from everyone except that trainer and admins, and they cannot be purchased — see [Create Trainee](../trainees/create.md). A service whose trainer has requested their own [account deletion](../../auth/delete-account-request.md) is hidden the same way, from the moment the request lands rather than when the account is disposed of; the trainer still sees their own services, so cancelling is not a hunt.

---

## Query Parameters
| Name         | Type   | Required | Description                                                             |
|--------------|--------|----------|-------------------------------------------------------------------------|
| `service_id` | string | No       | Filter by training service ID(s); comma-separated for multiple          |
| `user_id`    | string | No       | Filter by user IDs (comma-separated for multiple)                       |
| `category`   | string | No       | Filter by categories (comma-separated): `diet_plan`, `workout_plan`, `other` |
| `major_ids`  | string | No       | Filter by major IDs (comma-separated for multiple)                      |
| `search`     | string | No       | Search by title, description and trainer name. Max 255 characters. Persian-normalized — see the note below. |
| `page`       | int    | No       | Page number for pagination                                              |
| `sort`       | string | No       | `asc` for oldest, `desc` for latest (default: `desc`)                   |

> **`search` matching.** The term and the text it is matched against are both normalized first, so
> a service or trainer name stored with an Arabic keyboard's `ي`/`ك` is found by a search typed
> with the Persian `ی`/`ک` and vice versa; the same applies to hamza-bearing alefs, teh marbuta,
> zero-width joiners and non-joiners, the tatweel, Arabic diacritics, and Persian or Arabic-Indic
> digits (`۲۴` and `24` match each other). Matching is case-insensitive and matches anywhere in
> the text, not only at the start. **`%` and `_` are literal characters** — `?search=%` returns
> only services whose text actually contains a percent sign, not every service. A term that
> normalizes to nothing (whitespace alone) is treated as no filter at all. The trainer's name is
> matched from a copy held on the service, which is rewritten when the trainer renames, so a
> search by the new name finds their services and one by the old name does not.

> **Note:** Results are first sorted by marketing boosts; `sort` applies secondarily.

---

## Response

### 200 OK
Returns a paginated list of training service resources.

```json
{
  "data": [ { /* training service resource */ }, ... ],
  "links": { /* pagination data */ },
  "meta": { /* pagination data */ }
}
```

### 422 Unprocessable Entity
`search` was longer than 255 characters. See [Validation error](../../_globals/validation-errors.md).

See [Training Service Resource](training_service_resource.md) and [Pagination Data](../../_globals/pagination-data.md) (per page: 50).
