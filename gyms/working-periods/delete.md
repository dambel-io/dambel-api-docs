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
Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "Gym working period deleted successfully."
}
```

Localized from `messages.gyms.working_periods.deleted_successfully` (`fa`: “بازه کاری باشگاه با موفقیت حذف شد.”).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../../_globals/not-found-errors.md) |
