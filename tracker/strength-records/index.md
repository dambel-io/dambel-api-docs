# GET /api/v1/tracker/strength-records

List your own published strength-record claims.


---

## Permissions
| Permission                | Description                    |
|---------------------------|--------------------------------|
| `strength_records.view`   | View your strength-record claims |

Only your own claims. Other people's claims are read through
[the leaderboard](leaderboard.md), which is a different endpoint with a different permission.

---

## Query Parameters
| Name          | Type | Required | Description                                        |
|---------------|------|----------|----------------------------------------------------|
| `exercise_id` | int  | No       | Only claims for this exercise                      |
| `per_page`    | int  | No       | Results per page (default 50, **capped at 100**)   |
| `page`        | int  | No       | Page number for pagination                         |

Results are ordered by `claimed_at` descending. **Withdrawn claims are not listed** — withdrawing
is unpublishing, and a set is put back on the leaderboard by claiming it again rather than by
restoring anything.

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
- See [Strength Record Claim Resource](strength_record_claim_resource.md)
- See [Pagination Data](../../_globals/pagination-data.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
