# POST /api/v1/tracker/strength-records/{claim-id}/verifications

Verify another athlete's strength-record claim.


---

## Permissions
| Permission                | Description                                         |
|---------------------------|-----------------------------------------------------|
| `strength_records.view`   | Access the strength-record group                    |
| `strength_records.verify` | Verify a claim                                      |

**Any** authenticated user holding `strength_records.verify` may verify **anyone else's** claim.
Narrowing this to gym-mates or trainers would leave a new claim with nobody to attest to it.

You cannot verify your own claim — that is a **403**. A self-verified record is not evidence.

---

## Request Body Parameters
_None._ The claim is named in the URL and the verifier is the authenticated caller.

---

## Response

### 200 OK
```json
{
  "data": { /* strength record claim resource, with the new count */ }
}
```
The updated claim, so the client can re-render `verifications_count` and `verified_by_me` from the
same response.

**Verifying twice is a no-op.** A unique `(claim, verifier)` constraint in the database makes a
second row impossible — not a check-then-insert, which two concurrent requests would both win —
and the endpoint returns the existing state rather than an error.

A withdrawn claim can still be verified. It stays unpublished either way; verifying it does not
put it back on a leaderboard.

- See [Strength Record Claim Resource](strength_record_claim_resource.md)

---

## Notifications
The claimant receives `App\Notifications\Tracker\StrengthRecordVerifiedNotification`, **at most
once per hour per claim**. A claim that catches on collects verifications in bursts, and one push
per verification is how a good day becomes a reason to mute the app. The notification carries the
**running total**, not the verifier's name, so a suppressed verification is still reflected in
whatever the athlete eventually reads.

A repeat verification by the same peer never notifies at all.

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Missing permission, or the claim is your own | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not Found          | [Not found error](../../_globals/not-found-errors.md)           |

---
