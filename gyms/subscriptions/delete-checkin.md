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
No content is returned when the check-in is successfully deleted.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 404    | Not found (invalid gym, subscription, or check-in) |  |
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
