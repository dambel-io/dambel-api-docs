# GET /api/v1/gyms/administered

Lists the gyms the authenticated user administers — one row per delegation, with the gym, the permissions granted,
and whether the delegation is currently in effect.

This is the admin's own view. It is the counterpart to [`GET /gyms/{gym-id}/admins`](index.md), which is the
*owner's* view of one gym's roster.


---

## Permissions
Authentication only. No permission is required and none is checked: the query is scoped to the caller's own
`gym_admins` rows, so there is no other user's data to authorize against. A user who administers nothing gets an
empty page rather than a 403.

Note that the permissions listed on each row are what the *delegation* grants inside that gym — they say nothing
about whether the caller may read this endpoint.

---

## Query Parameters
| Name       | Type | Required | Description                                     | Example |
|------------|------|----------|-------------------------------------------------|---------|
| `per_page` | int  | No       | Rows per page, 1–100. Defaults to 50            | 20      |
| `page`     | int  | No       | Page number                                     | 2       |

---

## Response

### 200 OK
Returns a paginated list of gym admin resources, newest delegation first, each with its `gym` and `is_effective`.

#### Example
```json
{
  "data": [
    {
      "id": 1,
      "gym_id": 123,
      "title": "Front desk",
      "user_id": 42,
      "permissions": [17, 23],
      "permission_names": ["gym_plans.create", "gym_subscriptions.checkin"],
      "gym": { "id": 123, "name": "Iron Works", "...": "..." },
      "is_effective": true,
      "created_at": "2026-08-31T10:00:00.000000Z"
    }
  ],
  "links": { "...": "..." },
  "meta": { "...": "..." }
}
```

For the pagination envelope see [Pagination](../../_globals/pagination-data.md); for the row schema see
[Gym Admin Resource](gym_admin_resource.md) and [Gym Resource](../gym_resource.md).

**Rows where `is_effective` is `false` are still returned.** The delegation exists but grants nothing right now,
because the gym's owner no longer holds `gym_admins.view_own` — a premium feature. Showing the gym with the
delegation marked inactive is more useful than hiding it, since the admin's access returns the moment the owner
renews. Every action on such a gym will 403 until then.

---

### Error Responses
| Status | Description                      | Reference                                                        |
|--------|----------------------------------|------------------------------------------------------------------|
| 401    | Unauthorized (not authenticated) | [Authentication error](../../_globals/authentication-errors.md)  |
| 422    | Validation error (`per_page`)    | [Validation error](../../_globals/validation-errors.md)          |

---

## Related Resources
- [GET /api/v1/gyms/admin-permissions](delegatable-permissions.md) — the permissions an owner may delegate
- [GET /api/v1/gyms/{gym-id}/admins](index.md) — the owner's view of one gym's roster
- [Gym Admin Resource](gym_admin_resource.md)
- [Permissions](../../../permissions.md)
