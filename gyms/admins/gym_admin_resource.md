# Gym Admin Resource

Represents one delegation: a user who has been made an admin of a gym, with the permissions the owner granted them.


---

## Schema
| Field              | Type          | Description                                                                                  |
|--------------------|---------------|----------------------------------------------------------------------------------------------|
| `id`               | int           | Unique identifier for the gym admin                                                          |
| `gym_id`           | int           | ID of the gym                                                                                |
| `title`            | string\|null  | Free-text label for the role, e.g. "Front desk"                                              |
| `user_id`          | int           | ID of the user who is the admin                                                              |
| `permissions`      | int array     | Permission **IDs** granted to this admin. This is what is written and stored                 |
| `permission_names` | string array  | The same permissions resolved to their names, in the stored order. Read-only, derived        |
| `gym`              | object        | [Gym Resource](../gym_resource.md). Only present on [`GET /gyms/administered`](administered.md) |
| `is_effective`     | boolean       | Whether the delegation currently grants anything. Only present alongside `gym`                |
| `created_at`       | string (date) | When the delegation was created                                                              |

**`permissions` holds IDs, not names.** [`POST`](create.md) and [`PUT`](update.md) validate them with
`exists:permissions,id`. `permission_names` exists so a client can render a delegation without fetching the whole
permission table; an ID with no matching permission row is omitted from it rather than rendered as `null`, because
it grants nothing.

**Not every permission is delegatable.** Only the names published by
[`GET /gyms/admin-permissions`](delegatable-permissions.md) are ever consulted by a policy. Storing any other ID is
accepted but inert.

**`is_effective` is about the owner, not the admin.** `Gym::adminCan()` grants a delegated permission only while the
gym's *owner* still holds `gym_admins.view_own`, which is a premium feature. An owner whose subscription lapses
silently disables every admin they appointed. The field reports that so the client can say "inactive until the owner
renews" instead of showing buttons that would 403.

---

## Example
```json
{
  "id": 1,
  "gym_id": 123,
  "title": "Front desk",
  "user_id": 42,
  "permissions": [17, 23],
  "permission_names": ["gym_plans.create", "gym_subscriptions.checkin"],
  "created_at": "2026-08-31T10:00:00.000000Z"
}
```

On [`GET /gyms/administered`](administered.md) the same row additionally carries `gym` and `is_effective`.

---

## Related Resources
- [GET /api/v1/gyms/administered](administered.md) — the gyms the caller administers
- [GET /api/v1/gyms/admin-permissions](delegatable-permissions.md) — the permissions an owner may delegate
- [GET /api/v1/gyms/{gym-id}/admins](index.md) — a gym's admin roster
- [Permissions](../../../permissions.md) — roles, permissions and the gym-admin delegation model
