# DELETE /api/v1/gyms/{gym-id}/plans/{plan-id}

Deletes a specific subscription plan from a gym.


---

## Permissions
| Permission                | Description                                 |
|---------------------------|---------------------------------------------|
| `gym_plans.delete`        | Delete plans from your own gyms             |
| `gym_plans.delete_any`    | Delete plans from any gym                   |

---

## URL Parameters
| Name     | Type | Required | Description                | Example |
|----------|------|----------|----------------------------|---------|
| gym-id   | int  | Yes      | ID of the gym              | 123     |
| plan-id  | int  | Yes      | ID of the plan             | 55      |

---

## Request Example
```
DELETE /api/v1/gyms/123/plans/55
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
  "message": "Gym plan deleted successfully."
}
```

Localized from `messages.gyms.plans.deleted_successfully` (`fa`: “پلن باشگاه با موفقیت حذف شد.”).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../../_globals/not-found-errors.md) |
