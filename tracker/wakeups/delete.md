# DELETE /api/v1/tracker/wakeups/{tracker-wakeup-id}

Delete one of your wake-up records.


---

## Permissions
| Permission                | Description                 |
|---------------------------|-----------------------------|
| `tracker_wakeups.delete`  | Delete wake-up records      |

---

## URL Parameters
| Name                 | Type | Required | Description                     | Example |
|----------------------|------|----------|---------------------------------|---------|
| `tracker-wakeup-id`  | int  | Yes      | ID of the wake-up record        | 34      |

---

## Request Example
```
DELETE /api/v1/tracker/wakeups/34
```

---

## Response

### 204 No Content
Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "Wake-up record deleted successfully."
}
```

Localized from `messages.tracker.wakeups.deleted_successfully` (`fa`: “ثبت بیداری با موفقیت حذف شد.”).

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not found                 | [Not-found error](../../_globals/not-found-errors.md)           |

---
