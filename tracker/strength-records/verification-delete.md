# DELETE /api/v1/tracker/strength-records/{claim-id}/verifications

Take back your own verification of a strength-record claim.


---

## Permissions
| Permission                | Description                      |
|---------------------------|----------------------------------|
| `strength_records.view`   | Access the strength-record group |
| `strength_records.verify` | Verify and un-verify a claim     |

Only ever removes **your own** verification. Other peers' verifications of the same claim are
untouched.

---

## Request Body Parameters
_None._

---

## Response

### 200 OK
```json
{
  "data": { /* strength record claim resource, with the reduced count */ }
}
```
The updated claim rather than an empty body, because the number the client is about to re-render is
the verification count and this is the response that carries it.

Un-verifying something you never verified is a no-op that returns the same shape — the count is
simply unchanged. The row itself is hard-deleted; there is nothing about a withdrawn verification
worth keeping.

- See [Strength Record Claim Resource](strength_record_claim_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Missing permission, or the claim is your own | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not Found          | [Not found error](../../_globals/not-found-errors.md)           |

---
