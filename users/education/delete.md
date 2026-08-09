# DELETE /api/v1/users/{user-id}/education/{education-id}

Delete an education record from a user.


---

## Permissions
| Permission             | Description                                 |
|------------------------|---------------------------------------------|
| `education.delete`     | Delete your own education                   |
| `education.delete_any` | Delete education from any user              |

---

## Response

### 204 No Content
Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "Education deleted successfully."
}
```

Localized from `messages.users.education.deleted_successfully` (`fa`: “سوابق تحصیلی با موفقیت حذف شد.”).

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not found                 | [Not-found error](../../_globals/not-found-errors.md)           |

---
