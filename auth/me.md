# GET /api/v1/auth/me

Returns information about the currently authenticated user.


---

## Request Parameters
This endpoint does not accept any parameters.

---

## Request Example
```
GET /api/v1/auth/me
Authorization: Bearer {token}
```

---

## Response

### 200 OK
Returns the user resource and a list of permissions.

#### Example
```json
{
  "data": { /* user resource */ },
  "permissions": ["permission 1", "permission 2"]
}
```

For a full schema, see [User Resource](../users/user_resource.md).

The payload carries `is_trainer` and `is_gym_owner`, the user's own statement about which parts of the platform
apply to them. They shape what the client shows and **authorize nothing**; set them through
[`PUT /auth/me`](update-me.md).

The caller is always the subject here, so the payload includes the self-only fields — among them
`referrals_count` (how many users they directly referred) and `referral_score` (the weighted score over the whole
referral tree). The two are sourced differently and can briefly disagree; see
[Referral Score](../users/user_resource.md#referral-score).

The self-only fields also carry `deletion_requested_at` and `deletion_scheduled_at`. Both are `null` on a normal
account; both are set while a self-service deletion is pending, and `deletion_scheduled_at` is the date the account
will be disposed of. This is the endpoint a client polls to render a "your account is scheduled for deletion"
banner, with [`DELETE /api/v1/auth/delete-account`](delete-account-cancel.md) behind its undo button. See
[`POST /api/v1/auth/delete-account`](delete-account-request.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |

