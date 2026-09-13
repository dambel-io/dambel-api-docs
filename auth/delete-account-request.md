# POST /api/v1/auth/delete-account

Schedules the authenticated user's own account for deletion, after a grace period during which it can be restored.

- **Feature overview:** [Account Deletion](../../account-deletion.md) — the state machine, the grace period, and the purge/retain matrix
- **Authentication:** required (`auth:sanctum`)
- **Rate limit:** `throttle:5,1` — five calls per minute per user, the same budget as password reset. Every phase-1 call spends one SMS.

---

## Permissions
None. The subject is always the caller, so there is nothing to authorize against and the bearer token *is* the authorization boundary. This endpoint is unrelated to [`DELETE /api/v1/users/{user}`](../users/delete.md), the operator-only route, which still refuses to delete the caller's own account.

---

## Two phases on one endpoint

Deletion takes **two factors**: the password the user knows and the SIM they hold. Both phases are `POST` to this same URL and both require `current_password`; they are told apart by whether `confirmation_code` is present.

| Phase | Request | What happens | Response |
|-------|---------|--------------|----------|
| 1 — arm | `current_password` only | Blockers are evaluated **first**; if the account is clear, a six-digit code is sent by SMS to `users.phone` | `200` with `confirmation_required: true`, or `409` |
| 2 — commit | `current_password` **and** `confirmation_code` | The code is checked, the blockers are re-evaluated, the account is scheduled and every session is revoked | `202`, or `409`, or `422` |

The code expires **10 minutes** after it is sent. Re-running phase 1 replaces the previous code — only the newest one works.

Cancelling ([`DELETE /api/v1/auth/delete-account`](delete-account-cancel.md)) needs neither factor beyond the bearer token: it restores the account and destroys nothing.

---

## Request Body Parameters
| Name                | Type   | Required | Description                                                                          |
|---------------------|--------|----------|--------------------------------------------------------------------------------------|
| `current_password`  | string | Yes      | The caller's current password. Required in **both** phases.                          |
| `confirmation_code` | string | No       | Exactly 6 characters. Absent = phase 1 (send the code). Present = phase 2 (commit).  |

---

## Request Example

Phase 1:
```http
POST /api/v1/auth/delete-account
Authorization: Bearer {token}
Content-Type: application/json

{
  "current_password": "currentpassword123"
}
```

Phase 2:
```http
POST /api/v1/auth/delete-account
Authorization: Bearer {token}
Content-Type: application/json

{
  "current_password": "currentpassword123",
  "confirmation_code": "123456"
}
```

---

## Response

### 200 OK — phase 1, code sent
```json
{
  "message": "We sent a confirmation code to your phone.",
  "confirmation_required": true
}
```

Nothing is scheduled yet. The code is valid for 10 minutes.

---

### 202 Accepted — scheduled
```json
{
  "message": "Your account is scheduled for deletion.",
  "deletion_requested_at": "2026-09-11 10:00:00",
  "deletion_scheduled_at": "2026-09-25 10:00:00"
}
```

`202`, not `200`: the deletion is scheduled, not performed. `deletion_scheduled_at` is 14 days out (`config('users.deletion_grace_period_days')`).

**This is the last response the calling session ever sees.** Scheduling revokes *every* credential the user holds — all Sanctum tokens, including the one that made this call, and every Passport OAuth access, refresh and authorization-code row behind `/mcp` — so the next request on any of them returns `401`. A configured MCP client stops working for this account at the same moment. Clients must tear the session down locally rather than by calling [`POST /api/v1/auth/logout`](logout.md).

What happens at the moment of this response:

- The account disappears from [`GET /api/v1/users`](../users/index.md) and from [training-service search](../training/services/index.md) for everyone but holders of `users.view_all`.
- An `account_deletion_requested` notification is delivered.
- [`GET /api/v1/auth/me`](me.md) and [`POST /api/v1/auth/login`](login.md) both start reporting the pending state. Signing in still succeeds — that is how the user reaches the cancel endpoint.
- After the window elapses, a nightly sweep anonymizes the row and purges the personal data. Payments, gym subscriptions, ratings, comments and moderation reports survive, attached to an anonymized account that can no longer be found by the old name, username, email or phone.

**Repeating phase 1 on an account that is already pending returns this same `202` with the original dates, sends no SMS and does not move the deadline.**

---

### 409 Conflict — the account cannot be deleted yet
The payload is valid; the account's *state* is the conflict. Returned from **both** phases — phase 1 refuses before spending an SMS, and phase 2 re-checks because minutes have passed since.

```json
{
  "error": "This account cannot be deleted yet.",
  "code": "account_deletion_blocked",
  "blockers": [
    { "code": "gym_ownership", "message": "Transfer or close your gyms before deleting your account.", "count": 2 },
    { "code": "active_premium", "message": "Your premium subscription is still active.", "expires_at": "2026-12-01 00:00:00" }
  ]
}
```

`code` is always the constant `account_deletion_blocked`. `blockers` carries **every** blocker that applies, never just the first, so a user who clears one and retries does not then discover another. The array is ordered by the enum's declaration order below, not by evaluation order, so the client renders the same list every time.

| `code`               | Meaning                                                                                        | Extra keys                          |
|----------------------|------------------------------------------------------------------------------------------------|-------------------------------------|
| `gym_ownership`      | The user owns one or more gyms.                                                                 | `count` (integer)                   |
| `unsettled_balance`  | The wallet balance is not zero — positive *or* negative.                                        | `balance` (number)                  |
| `pending_withdrawal` | A withdrawal request is neither paid nor rejected.                                              | `count` (integer)                   |
| `active_premium`     | A premium subscription is still running.                                                        | `expires_at` (string, date-time)    |
| `active_trainees`    | Trainees on a sold training service have not been delivered.                                    | `count` (integer)                   |

Every blocker is **hard** — none is advisory, and there is no override. A client reads `code` and may treat the extra keys as optional; `message` is localized by `Accept-Language`. The `code` values are a client contract: renaming one is a breaking change.

---

## Error Responses
| Status | Description                                     | Reference / Example                                                 |
|--------|-------------------------------------------------|---------------------------------------------------------------------|
| 401    | Not authenticated                               | [Authentication error](../_globals/authentication-errors.md)        |
| 422    | Validation error, or a rejected confirmation code | See below                                                          |
| 429    | Too many requests                               | [Rate-limit error](../_globals/rate-limit-errors.md)                |
| 500    | The SMS could not be sent — nothing was scheduled | `{ "message": "Failed to send SMS. Please try again." }`           |

#### 422 — wrong password
```json
{
  "message": "The password is incorrect.",
  "errors": {
    "current_password": ["The password is incorrect."]
  }
}
```

#### 422 — wrong, expired or never-issued confirmation code
```json
{
  "message": "Invalid verification code.",
  "errors": {
    "confirmation_code": ["Invalid verification code."]
  }
}
```

One answer covers all three cases, so the response cannot be used to probe whether a deletion request is in flight. A `confirmation_code` that is not exactly 6 characters is rejected by validation with the standard `errors` shape before it is ever checked.

---

## Related Resources
- [`DELETE /api/v1/auth/delete-account`](delete-account-cancel.md) — take the request back inside the window
- [`GET /api/v1/auth/me`](me.md) — read the pending-deletion timestamps
- [`POST /api/v1/auth/login`](login.md) — signing in during the window succeeds and is flagged
- [`PUT /api/v1/auth/change-password`](change-password.md) — the same `current_password` re-authentication rule
