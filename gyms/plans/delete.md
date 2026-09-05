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

### 400 Bad Request — the plan has subscriptions
A plan that anyone has ever subscribed to cannot be deleted: `gym_subscriptions.gym_plan_id` is not nullable, so the
delete would take every subscription — and the check-ins hanging off them — with it. Set `is_active` to `false` with
`PUT /api/v1/gyms/{gym-id}/plans/{plan-id}` instead; an inactive plan is hidden from the gym's plan list while its
existing subscribers keep their memberships.

`attached_data` reports what is blocking the delete.

```json
{
  "error": "This plan has subscriptions and cannot be deleted. Deactivate it instead.",
  "attached_data": {
    "subscriptions": 3,
    "total": 3
  }
}
```

Localized from `messages.gyms.plans.cannot_be_deleted_with_subscriptions`
(`fa`: “این پلن اشتراک دارد و قابل حذف نیست. به جای آن غیرفعالش کنید.”).

---

### Error Responses
| Status | Description                       | Reference                                      |
|--------|-----------------------------------|------------------------------------------------|
| 400    | Plan has subscriptions            | See above                                      |
| 401    | Unauthorized                      | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)         | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                         | [Not-found error](../../_globals/not-found-errors.md) |
