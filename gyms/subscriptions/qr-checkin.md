# POST /api/v1/gyms/{gym-id}/subscriptions/checkin/{subscription-id}/qr

Creates a check-in by redeeming a QR token displayed by the gym (see
[issue check-in token](issue-checkin-token.md)). A live gym-side token is the gym's attestation, so
**`gym_approved` is always `true`**. **`user_approved` is `true` only when the caller is the
subscriber** — the intended athlete-scans-the-kiosk flow, which therefore records a mutually approved
visit in one call. A gym admin redeeming on a member's behalf records `user_approved: false`: minting
and redeeming a token are the same permission, so the gym cannot be allowed to assert the athlete's
side of a visit. The [manual check-in](checkin.md) derives both flags from the caller in the same way.


---

## Permissions

Same as [manual check-in](checkin.md): the subscriber themselves, or a gym admin holding the
delegated `gym_subscriptions.checkin` permission.

---

## URL Parameters
| Name            | Type | Required | Description            | Example |
|-----------------|------|----------|------------------------|---------|
| gym-id          | int  | Yes      | ID of the gym          | 123     |
| subscription-id | int  | Yes      | ID of the subscription | 456     |

---

## Request Body Parameters
| Name  | Type   | Required | Description                                    | Example        |
|-------|--------|----------|------------------------------------------------|----------------|
| token | string | Yes      | The plaintext token scanned from the gym's QR code (max 64 chars) | "kW3n8b2Xq…"   |
| notes | string | No       | Optional note for the check-in (max 2000)      | "Arrived late" |

---

## Request Example
```json
{
  "token": "kW3n8b2XqL0pT7vYcRfZ9aH1mJ4sD6eGuI5oPxQw",
  "notes": "Arrived late"
}
```

---

## Response

### 201 Created
Returns the created check-in resource with both approval flags `true`. The gym owner is notified.

For a full schema, see [Gym Subscription Check-in Resource](gym_subscription_checkin_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 404    | Gym and subscription do not match | |
| 400    | An open check-in already exists | |
| 400    | Invalid token — expired, tampered, or issued for another gym (one message for all three) | |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 422    | Validation error           | [Validation error](../../_globals/validation-errors.md) |
| 429    | Throttled (10/min)         |                                                |
