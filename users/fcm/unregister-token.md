# `POST /api/v1/users/fcm/unregister-token`

Unregister an FCM token for the authenticated user to stop receiving push notifications from that device.


---

## Authentication
This endpoint requires authentication via Sanctum token.

---

## Request Body Parameters
| Name    | Type   | Required | Description            |
|---------|--------|----------|------------------------|
| `token` | string | Yes      | FCM registration token |

---

## Response

### 200 OK
```
{
  "message": "FCM token unregistered successfully"
}
```

---

## Error Responses
- **422 Unprocessable Entity:** [Validation error](../../_globals/validation-errors.md)
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)

---

## Notes
- This will remove the FCM token from the user's registered devices
- The user will no longer receive push notifications on the device associated with this token
