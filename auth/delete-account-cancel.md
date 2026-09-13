# DELETE /api/v1/auth/delete-account

Takes a pending account deletion back, restoring the account completely. Valid at any point inside the grace period.

- **Feature overview:** [Account Deletion](../../account-deletion.md) — the state machine, the grace period, and the purge/retain matrix
- **Authentication:** required (`auth:sanctum`)
- **Rate limit:** `throttle:5,1`

---

## Permissions
None. The subject is always the caller.

**No password and no SMS code, deliberately.** Cancelling is the restorative direction: it destroys nothing and puts the account back exactly as it was, so the bearer token is sufficient. A second factor would only give a user racing their own deletion deadline a way to fail — the one outcome the grace period exists to prevent. Requesting the deletion ([`POST /api/v1/auth/delete-account`](delete-account-request.md)) is where both factors are demanded.

Requesting a deletion revokes every session the user held, so the token used here is normally one minted by a fresh [`POST /api/v1/auth/login`](login.md), which keeps working during the window.

---

## Request Body Parameters
None.

---

## Request Example
```http
DELETE /api/v1/auth/delete-account
Authorization: Bearer {token}
```

---

## Response

### 200 OK
```json
{
  "message": "Your account deletion has been cancelled."
}
```

`deletion_requested_at` and `deletion_scheduled_at` are cleared, any unused confirmation code is dropped, the account reappears in [`GET /api/v1/users`](../users/index.md) and in [training-service search](../training/services/index.md), and an `account_deletion_cancelled` notification is delivered. The session used to cancel stays valid; sessions revoked when the deletion was requested are **not** restored.

---

## Error Responses
| Status | Description                                        | Reference / Example                                            |
|--------|----------------------------------------------------|-----------------------------------------------------------------|
| 401    | Not authenticated                                  | [Authentication error](../_globals/authentication-errors.md)   |
| 404    | No deletion is pending, or the account is already disposed of | `{ "error": "Item not found." }`                     |
| 429    | Too many requests                                  | [Rate-limit error](../_globals/rate-limit-errors.md)           |

`404` rather than `409`: an account whose grace period has already elapsed and been swept has nothing left to restore, and the response confirms no state the caller has not already been told about.

---

## Related Resources
- [`POST /api/v1/auth/delete-account`](delete-account-request.md) — request the deletion
- [`GET /api/v1/auth/me`](me.md) — read the pending-deletion timestamps
