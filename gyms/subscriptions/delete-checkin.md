# DELETE /api/v1/gyms/{gym-id}/subscriptions/delete-checkin/{subscription-id}/{checkin-id}

Deletes a check-in record from a gym subscription.


---

## Permissions
| Permission                          | Description                                 |
|-------------------------------------|---------------------------------------------|
| `gym_subscription_checkins.delete`  | Delete check-ins for your own gyms          |
| `gym_subscription_checkins.delete_any` | Delete check-ins for any gym               |

---

## URL Parameters
| Name            | Type | Required | Description                | Example |
|-----------------|------|----------|----------------------------|---------|
| gym-id          | int  | Yes      | ID of the gym              | 123     |
| subscription-id | int  | Yes      | ID of the subscription     | 456     |
| checkin-id      | int  | Yes      | ID of the check-in         | 789     |

---

## Request Example
```
DELETE /api/v1/gyms/123/subscriptions/delete-checkin/456/789
Authorization: Bearer {token}
```

---

## Response

### 204 No Content
Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "Gym subscription check-in deleted successfully."
}
```

Localized from `messages.gyms.subscriptions.checkins.deleted_successfully` (`fa`: “چک‌این اشتراک باشگاه با موفقیت حذف شد.”).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 404    | Not found (invalid gym, subscription, or check-in) |  |
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
