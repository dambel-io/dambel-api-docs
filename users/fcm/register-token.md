# POST /api/v1/users/fcm/register-token

Register an FCM token for the authenticated user to receive push notifications.


---

## Authentication
This endpoint requires authentication via Sanctum token.

---

## Request Body Parameters
| Name          | Type   | Required | Description                          |
|---------------|--------|----------|--------------------------------------|
| `token`       | string | Yes      | FCM registration token               |
| `device_type` | string | No       | Device type (`ios`, `android`, `web`)|
| `device_id`   | string | No       | Unique device identifier             |
| `language`    | string | No       | Device language code (e.g. `en`, `fa`). Push notifications will be sent in this language. |

---

## Response

### 200 OK
```
{
  "message": "FCM token registered successfully"
}
```

---

## Error Responses
| Status | Description      | Reference                                                       |
|--------|------------------|-----------------------------------------------------------------|
| 422    | Validation error | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized     | [Authentication error](../../_globals/authentication-errors.md) |

---

## Notes
- If the token already exists for the user, it will be updated with the new device information
- Multiple devices per user are supported
- Tokens are used for sending push notifications via Firebase Cloud Messaging
- When `language` is provided, push notification content (title and body) will be sent in that language for the specific device
- If a user has devices with different languages, each device receives the notification translated to its registered language
