# GET /api/v1/gyms/{gym-id}/admins

Retrieves a list of admins for a specific gym.


---

## Permissions
| Permission             | Description                                         |
|------------------------|-----------------------------------------------------|
| `gym_admins.view_own`  | View admins list for your own gym                   |
| `gym_admins.view_all`  | View admins list for all gyms (admin only)          |

---

## Path Parameters
| Name    | Type | Required | Description           | Example |
|---------|------|----------|-----------------------|---------|
| gym-id  | int  | Yes      | ID of the gym         | 123     |

---

## Response

### 200 OK
Returns a list of gym admin resources.

#### Example
```json
{
  "data": [
    {
      "id": 1,
      "gym_id": 123,
      "title": "Manager",
      "user_id": 42,
      "permissions": [17, 23],
      "permission_names": ["gym_plans.create", "gym_subscriptions.checkin"],
      "created_at": "2026-08-31T10:00:00.000000Z"
    }
  ]
}
```

`permissions` holds permission **IDs**; `permission_names` is the same set resolved to names so a client can render
the roster without fetching the permission table. Only the names published by
[`GET /gyms/admin-permissions`](delegatable-permissions.md) are ever consulted by a policy. This endpoint does not
emit `gym` or `is_effective` — every row already belongs to the gym in the URL; see
[`GET /gyms/administered`](administered.md) for the admin's own view.

For a full schema, see [Gym Admin Resource](gym_admin_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../../_globals/not-found-errors.md) |
