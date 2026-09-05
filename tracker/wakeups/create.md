# POST /api/v1/tracker/wakeups

Record a wake-up. The record is always attributed to the authenticated user.


---

## Permissions
| Permission                | Description                 |
|---------------------------|-----------------------------|
| `tracker_wakeups.create`  | Create wake-up records      |

---

## Request Body Parameters
| Name         | Type   | Required | Description                                      |
|--------------|--------|----------|--------------------------------------------------|
| `tracked_at` | date   | Yes      | When the wake-up happened                        |
| `notes`      | string | No       | Optional notes (max 2000)                        |

---

## Request Example
```json
POST /api/v1/tracker/wakeups

{
  "tracked_at": "2026-08-31 07:15:00",
  "notes": "Slept well."
}
```

---

## Response

### 201 Created
```json
{
  "data": { /* tracker wakeup resource */ }
}
```
- [Tracker Wakeup Resource](tracker_wakeup_resource.md)

> Viewers of a shared tracker that both includes wake-ups (`include_wakeup`) and asks to be notified
> about them (`notify_wakeup`), and whose date range covers `tracked_at`, receive a `UserWokeUpNotification`.

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 422    | Validation error          | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |

---
