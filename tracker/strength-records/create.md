# POST /api/v1/tracker/strength-records

Publish one logged workout set as a strength-record claim.


---

## Permissions
| Permission                  | Description                     |
|-----------------------------|---------------------------------|
| `strength_records.view`     | Access the strength-record group |
| `strength_records.create`   | Publish a claim                 |

---

## Request Body Parameters
| Name                     | Type    | Required | Description                                     |
|--------------------------|---------|----------|-------------------------------------------------|
| `tracker_workout_set_id` | integer | Yes      | A set **you** logged, carrying an exercise and a rep count |

`user_id`, `exercise_id`, `rep_count` and `weight` are never read from the request. The last three
are copied from the set server-side, once, and are not updated afterwards — see
[Strength Record Claim Resource](strength_record_claim_resource.md).

Nothing an athlete logs is public until this endpoint is called. A user who has never claimed a set
does not appear on any leaderboard.

---

## Response

### 201 Created
```json
{
  "data": { /* strength record claim resource */ }
}
```

### 200 OK
Returned when the set already had a claim that you had withdrawn. The **same** claim is
republished — `withdrawn_at` goes back to `null` and the existing verification count is kept, so
withdrawing and re-claiming is not a way to reset a count.

- See [Strength Record Claim Resource](strength_record_claim_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 422    | Validation Error. Also returned when the set carries no exercise or no rep count and therefore cannot be ranked. | [Validation error](../../_globals/validation-errors.md) |
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |
| 404    | The set is not yours. A set belonging to someone else and a set that does not exist return the same 404, so the endpoint cannot be used to discover which set IDs exist. | [Not found error](../../_globals/not-found-errors.md) |

---
