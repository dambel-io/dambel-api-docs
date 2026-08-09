# DELETE /api/v1/users/{user-id}/championships/{championship-id}

Delete a championship record from a user.


---

## Permissions
| Permission                  | Description                                 |
|-----------------------------|---------------------------------------------|
| `championships.delete`      | Delete your own championships               |
| `championships.delete_any`  | Delete championships from any user          |

---

## Response

### 204 No Content
Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "Championship deleted successfully."
}
```

Localized from `messages.users.championships.deleted_successfully` (`fa`: “مسابقه قهرمانی با موفقیت حذف شد.”).

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not found                 | [Not-found error](../../_globals/not-found-errors.md)           |

---
