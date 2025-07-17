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
No content is returned when the plan is successfully deleted.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../../_globals/not-found-errors.md) |
