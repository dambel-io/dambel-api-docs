# DELETE /api/v1/admin/roles/{role-id}

Delete a role.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `roles.view_all`      | Access roles        |
| `roles.delete`        | Delete role         |

---

## Response

### 204 No Content
Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "Role deleted successfully."
}
```

Localized from `messages.admin.roles.deleted_successfully` (`fa`: “نقش با موفقیت حذف شد.”).

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not found                 | [Not-found error](../../_globals/not-found-errors.md)           |

---
