# POST /api/v1/gyms/{gym-id}/subscriptions/checkout/{subscription-id}/qr

Closes the subscription's open check-in by redeeming a QR token displayed by the gym (see
[issue check-in token](issue-checkin-token.md)). A live gym-side token is the gym's attestation, so
**`gym_approved` becomes `true`** even if the check-in was recorded one-sided. **`user_approved` is
raised only when the caller is the subscriber**, and is never lowered — a gym admin closing the visit
can neither assert nor retract the athlete's side of it.


---

## Permissions

Same as [manual check-out](checkout.md): the subscriber themselves, or a gym admin holding the
delegated `gym_subscriptions.checkin` permission.

---

## URL Parameters
| Name            | Type | Required | Description            | Example |
|-----------------|------|----------|------------------------|---------|
| gym-id          | int  | Yes      | ID of the gym          | 123     |
| subscription-id | int  | Yes      | ID of the subscription | 456     |

---

## Request Body Parameters
| Name  | Type   | Required | Description                                       | Example      |
|-------|--------|----------|---------------------------------------------------|--------------|
| token | string | Yes      | The plaintext token scanned from the gym's QR code (max 64 chars) | "kW3n8b2Xq…" |

---

## Request Example
```json
{
  "token": "kW3n8b2XqL0pT7vYcRfZ9aH1mJ4sD6eGuI5oPxQw"
}
```

---

## Response

### 200 OK
The token is validated **before** the check-in is touched — an invalid scan never mutates the open
check-in. The gym owner is notified.

#### Example
```json
{
  "message": "Checked out successfully."
}
```

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 404    | Gym and subscription do not match | |
| 400    | Invalid token — expired, tampered, or issued for another gym (one message for all three) | |
| 400    | No open check-in to close  | |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 422    | Validation error           | [Validation error](../../_globals/validation-errors.md) |
| 429    | Throttled (10/min)         |                                                |
