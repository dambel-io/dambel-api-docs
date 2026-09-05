# DELETE /api/v1/tracker/strength-records/{claim-id}

Withdraw a strength-record claim. The record leaves every leaderboard on this request.


---

## Permissions
| Permission                     | Description                                   |
|--------------------------------|-----------------------------------------------|
| `strength_records.view`        | Access the strength-record group              |
| `strength_records.delete`      | Withdraw **your own** claim                   |
| `strength_records.delete_any`  | Withdraw anyone's claim (operators; used to take down a claim that a report has confirmed fraudulent) |

---

## Request Body Parameters
_None._

---

## Response

### 204 No Content
**Nothing is deleted.** The claim's `withdrawn_at` is set, and:

- its verifications are **kept** — they are other people's statements, and destroying them would
  make withdraw-then-reclaim a way to reset an unflattering count;
- claiming the same set again republishes this same claim, with that count intact.

To remove a claim entirely, delete the workout set it attests to; the claim and its verifications
cascade away with it.

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not Found          | [Not found error](../../_globals/not-found-errors.md)           |

---
