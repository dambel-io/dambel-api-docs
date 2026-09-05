# PUT /api/v1/tracker/wakeups/{tracker-wakeup-id}

Update one of your wake-up records.


---

## Permissions
| Permission                | Description                 |
|---------------------------|-----------------------------|
| `tracker_wakeups.update`  | Update wake-up records      |

---

## URL Parameters
| Name                 | Type | Required | Description                     | Example |
|----------------------|------|----------|---------------------------------|---------|
| `tracker-wakeup-id`  | int  | Yes      | ID of the wake-up record        | 34      |

---

## Request Body Parameters
| Name         | Type   | Required | Description                                              |
|--------------|--------|----------|----------------------------------------------------------|
| `tracked_at` | date   | No       | When the wake-up happened                                |
| `notes`      | string | No       | Optional notes (max 2000); send `null` to clear them     |

*All parameters are optional. If omitted, they are not updated.*

---

## Request Example
```json
PUT /api/v1/tracker/wakeups/34

{
  "notes": null
}
```

---

## Response

### 200 OK
```json
{
  "data": { /* tracker wakeup resource */ }
}
```
- [Tracker Wakeup Resource](tracker_wakeup_resource.md)

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 422    | Validation error          | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not found                 | [Not-found error](../../_globals/not-found-errors.md)           |

---
