# DELETE /api/v1/users/{user-id}/detach-role/{role-id}

Detach a role from a user.


---

## Permissions
| Permission          | Description                                   |
|---------------------|-----------------------------------------------|
| `users.detach_role` | Detach a role from any user except themselves |

---

## Response

### 204 No Content
Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "Role detached successfully."
}
```

Localized from `messages.users.role_detached_successfully` (`fa`: “نقش با موفقیت حذف شد.”).

---

## Error Responses
| Status | Description                          | Reference                                                    |
|--------|--------------------------------------|--------------------------------------------------------------|
| 400    | User does not have this role         |                                                              |
| 401    | Unauthorized                         | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden                            | [Permission error](../_globals/permission-errors.md)         |
| 404    | Role or user not found               | [Not-found error](../_globals/not-found-errors.md)           |
