# DELETE /api/v1/users/{user-id}

Delete a user from the system.


---

## Permissions
| Permission         | Description           |
|--------------------|----------------------|
| `users.delete_any` | Delete any user      |

> **Disabled by default.** `users.delete_any` is defined in `config/permission.php` but assigned to **no role**, because user accounts must not be hard-deleted (data integrity and the activity-log audit trail depend on it). Every caller therefore gets a `403`. The endpoint, policy and tests are kept intact — granting the permission to a role in `config/permission.php` and re-running `PlatformDataSeeder` re-enables it.

Beyond the permission, the policy also refuses when the target is at the same access level (also holds `users.delete_any`) or is the caller themselves.

---

## Response

### 204 No Content
Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "User deleted successfully."
}
```

Localized from `messages.users.deleted_successfully` (`fa`: “کاربر با موفقیت حذف شد.”).

---

## Error Responses
| Status | Description               | Reference                                                    |
|--------|---------------------------|--------------------------------------------------------------|
| 401    | Unauthorized              | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../_globals/permission-errors.md)         |
| 404    | Not found                 | [Not-found error](../_globals/not-found-errors.md)           |

---
