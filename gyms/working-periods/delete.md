# DELETE /api/v1/gyms/{gym-id}/working-periods/{working-period-id}

Deletes a specific working period from a gym.


---

## Permissions
| Permission                    | Description                                 |
|-------------------------------|---------------------------------------------|
| `gym_working_periods.delete`  | Delete working periods from your own gyms   |
| `gym_working_periods.delete_any` | Delete working periods from any gym        |

---

## URL Parameters
| Name              | Type | Required | Description                | Example |
|-------------------|------|----------|----------------------------|---------|
| gym-id            | int  | Yes      | ID of the gym              | 123     |
| working-period-id | int  | Yes      | ID of the working period   | 55      |

---

## Request Example
```
DELETE /api/v1/gyms/123/working-periods/55
Authorization: Bearer {token}
```

---

## Response

### 204 No Content
No content is returned when the working period is successfully deleted.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../../_globals/not-found-errors.md) |
