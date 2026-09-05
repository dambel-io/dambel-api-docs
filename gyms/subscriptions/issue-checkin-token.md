# POST /api/v1/gyms/{gym-id}/checkin-token

Rotates the gym's QR check-in code and returns the new plaintext token. The gym displays this token
(typically as a QR code on a kiosk screen); athletes scan it and redeem it against their own
subscription via [QR check-in](qr-checkin.md) / [QR check-out](qr-checkout.md).


---

## Security parameters

- **TTL:** each token expires **2 minutes** after issuance.
- **Rotation:** every call issues a fresh token. Previously issued tokens stay valid until their own
  expiry, so a code already on screen does not die mid-scan; expired rows are pruned on each call.
- **Storage:** only a SHA-256 hash of the token is stored. The plaintext in the response is shown once.
- **Throttle:** 30 requests/minute — sized for a kiosk polling for the next code.
- **Redemption idempotence:** one displayed code may be redeemed by many athletes, but a subscription
  with an open check-in cannot check in again (400).

---

## Permissions
| Permission                  | Description                                                        |
|-----------------------------|--------------------------------------------------------------------|
| `gym_subscriptions.checkin` | Gym owner — or a gym admin delegated this permission — may rotate the code |

---

## URL Parameters
| Name   | Type | Required | Description   | Example |
|--------|------|----------|---------------|---------|
| gym-id | int  | Yes      | ID of the gym | 123     |

---

## Request Body Parameters

None.

---

## Response

### 201 Created

#### Example
```json
{
  "data": {
    "token": "kW3n8b2XqL0pT7vYcRfZ9aH1mJ4sD6eGuI5oPxQw",
    "expires_at": "2026-09-02 10:32:00"
  }
}
```

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 403    | Forbidden (not the owner or a delegated admin) | [Permission error](../../_globals/permission-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 429    | Throttled (30/min)         |                                                |
