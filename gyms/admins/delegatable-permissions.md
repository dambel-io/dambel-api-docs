# GET /api/v1/gyms/admin-permissions

Lists the permissions a gym owner may delegate to a gym admin. This is the set an owner's picker should offer when
creating or updating an admin.


---

## Permissions
Authentication only. The response is platform reference data — the fixed set of names the gym policies consult — so
it is not scoped to any caller and no permission is required.

---

## Query Parameters
None. The full set is returned; it is nineteen names and does not paginate.

---

## Response

### 200 OK
Returns the delegatable permissions in a stable order, as
[Permission Resources](../../admin/permissions/permission_resource.md).

#### Example
```json
{
  "data": [
    { "id": 31, "name": "gym_buffet_items.create" },
    { "id": 32, "name": "gym_buffet_items.delete" },
    { "id": 33, "name": "gym_buffet_items.update" },
    { "id": 17, "name": "gym_plans.create" },
    { "id": 23, "name": "gym_subscriptions.checkin" }
  ]
}
```

**This is deliberately not the whole permission table.** A gym admin's `permissions` array can hold any permission
ID — [`POST /gyms/{gym-id}/admins`](create.md) validates only `exists:permissions,id` — but `Gym::adminCan()` is the
single place a delegated permission is ever consulted, and it is only ever asked about these nineteen names. An ID
outside this set is stored and returned faithfully and grants nothing. Offering only this set is what keeps an
owner from granting something that silently does not work.

The set is the exact list of names passed to `Gym::adminCan()` across `app/Policies`, held as
`GymAdmin::DELEGATABLE_PERMISSIONS` and re-derived from those call sites by a test, so the two cannot drift apart.

**Delegation only works while the owner is premium.** `Gym::adminCan()` additionally requires the gym's owner to
hold `gym_admins.view_own`. See `is_effective` on [Gym Admin Resource](gym_admin_resource.md).

---

### Error Responses
| Status | Description                      | Reference                                                        |
|--------|----------------------------------|------------------------------------------------------------------|
| 401    | Unauthorized (not authenticated) | [Authentication error](../../_globals/authentication-errors.md)  |

---

## Related Resources
- [POST /api/v1/gyms/{gym-id}/admins](create.md) — create a delegation
- [PUT /api/v1/gyms/{gym-id}/admins/{admin-id}](update.md) — change a delegation
- [GET /api/v1/gyms/administered](administered.md) — the admin's own view
- [Permissions](../../../permissions.md)
