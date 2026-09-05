# PUT /api/v1/gyms/{gym-id}/admins/{admin-id}

Updates a gym admin's information. All parameters are optional; only provided fields will be updated. You can set fields to null to clear them.


---

## Permissions
| Permission             | Description                                         |
|------------------------|-----------------------------------------------------|
| `gym_admins.update`    | Update gym admins of your own gyms                  |
| `gym_admins.update_any`| Update gym admins for any gym (admin only)          |

---

## Path Parameters
| Name      | Type | Required | Description           | Example |
|-----------|------|----------|-----------------------|---------|
| gym-id    | int  | Yes      | ID of the gym         | 123     |
| admin-id  | int  | Yes      | ID of the admin to update | 5   |

---

## Request Body Parameters
| Name        | Type         | Required | Description                                 | Example                |
|-------------|--------------|----------|---------------------------------------------|------------------------|
| title       | string       | No       | Title of the admin (max 255 characters)     | "Manager"             |
| permissions | int array    | No      | Permission **IDs** to grant. Each must exist (`exists:permissions,id`). Only the IDs published by [`GET /gyms/admin-permissions`](delegatable-permissions.md) do anything | [17, 23] |

---

## Request Example
```json
{
  "title": "Manager",
  "permissions": [17, 23]
}
```

Passing an ID outside the delegatable set is accepted and stored, and grants nothing — `Gym::adminCan()` is
only ever asked about the published names.

---

## Response

### 200 OK
Returns the updated gym admin resource.

#### Example
```json
{
  "id": 1,
  "gym_id": 123,
  "title": "Manager",
  "user_id": 42,
  "permissions": [17, 23],
  "permission_names": ["gym_plans.create", "gym_subscriptions.checkin"],
  "created_at": "2026-08-31T10:00:00.000000Z"
}
```

For a full schema, see [Gym Admin Resource](gym_admin_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 422    | Validation error           | [Validation error](../../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
