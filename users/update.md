# PUT /api/v1/users/{user-id}

Update the information of a specific user.


---

## Permissions
| Permission         | Description                 |
|--------------------|-----------------------------|
| `users.update_any` | Update any user as an admin |

---

## Request Body Parameters
| Name         | Type    | Required | Description                             |
|--------------|---------|----------|-----------------------------------------|
| `first_name` | string  | No       | First name (max 255)                    |
| `last_name`  | string  | No       | Last name (max 255)                     |
| `email`      | string  | No       | Email (max 255, unique)                 |
| `phone`      | string  | No       | Phone number (unique, E.164 format). **Operator-only in practice** — there is no self-service equivalent on [`PUT /auth/me`](../auth/update-me.md), because a phone number is an authentication factor and changing it needs OTP re-verification that does not exist yet. |
| `bank_account_number` | string | No | Bank account number (max 50 characters, nullable) |
| `username`   | string  | No       | Username (max 255, unique; letters, digits, `_` and `.` only — `/^[a-zA-Z0-9_.]+$/`) |
| `height`     | integer | No       | User's height in CM                     |
| `birth_date` | date    | No       | User's birth date                       |
| `gender` | string    | No       | User's gender (`male`, `female`, `other`)                 |
| `password`   | string  | No       | New password (will be hashed)           |
| `trainer_license_image` | null | No | Only `null` is accepted, which clears the license. Any other value is rejected with 422 — uploads go through [Create Media](../media/create.md) with `purpose=trainer_license` |
| `trainer_license_approved` | boolean\|null | No | The review decision: `true` approves, `false` rejects, `null` returns the user to pending |
| `trainer_license_rejection_reason` | string\|null | No | Reason shown to the user when rejected (max 1000) |

*All parameters are optional. If omitted, they will not be updated.*

**`is_trainer` and `is_gym_owner` are not accepted here, and that is deliberate.** They are the user's own statement about which parts of the platform apply to them, so they are settable only on [`PUT /auth/me`](../auth/update-me.md). Sending them to this endpoint has no effect — they are silently ignored, not rejected, because they are not operator fields at all. This is the mirror image of `phone` above: each endpoint deliberately owns the fields that belong to it. Neither flag authorizes anything, so an operator has no reason to need them.

### Trainer license review
Setting `trainer_license_approved` to a non-null value that differs from the user's current decision sends them a `TrainerLicenseReviewedNotification` (see [Notifications](../../notifications.md)). Re-sending the same decision is a no-op and notifies nobody.

Clearing `trainer_license_image` deletes the stored document and resets both `trainer_license_approved` and `trainer_license_rejection_reason` to `null`, unless the same request sets them explicitly.

---

## Response

### 200 OK
Returns the updated user resource.

```json
{
  "data": { /* user resource */ }
}
```

See [User Resource](user_resource.md).

---

## Error Responses
| Status | Description                       | Reference                                                    |
|--------|-----------------------------------|--------------------------------------------------------------|
| 404    | User not found                    | [Not-found error](../_globals/not-found-errors.md)           |
| 409    | Email or phone already in use     |                                                              |
| 422    | Validation error                  | [Validation error](../_globals/validation-errors.md)         |
| 401    | Unauthorized                      | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden                         | [Permission error](../_globals/permission-errors.md)         |
