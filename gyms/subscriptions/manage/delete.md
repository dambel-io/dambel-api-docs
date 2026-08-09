# DELETE /api/v1/gyms/{gym-id}/subscriptions/manage/{subscription-id}

Deletes a subscription for a user in a specific gym.


---

## Permissions
| Permission                    | Description                                 |
|-------------------------------|---------------------------------------------|
| `gym_subscriptions.delete`    | Delete subscriptions for your own gyms      |
| `gym_subscriptions.delete_any`| Delete subscriptions for any gym            |

---

## URL Parameters
| Name             | Type | Required | Description                | Example |
|------------------|------|----------|----------------------------|---------|
| gym-id           | int  | Yes      | ID of the gym              | 123     |
| subscription-id  | int  | Yes      | ID of the subscription     | 456     |

---

## Request Example
```
DELETE /api/v1/gyms/123/subscriptions/manage/456
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
  "message": "Gym subscription deleted successfully."
}
```

Localized from `messages.gyms.subscriptions.deleted_successfully` (`fa`: “اشتراک باشگاه با موفقیت حذف شد.”).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 404    | Not found (invalid gym or subscription) |  |
| 401    | Unauthorized               | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../../_globals/permission-errors.md) |
