# POST /api/v1/gyms/{gym-id}/admins

Creates a new admin for a gym.


---

## Permissions
| Permission             | Description                                         |
|------------------------|-----------------------------------------------------|
| `gym_admins.create`    | Create admins for your own gyms                     |
| `gym_admins.create_any`| Create admins for any gym (admin only)              |

---

## Path Parameters
| Name    | Type | Required | Description           | Example |
|---------|------|----------|-----------------------|---------|
| gym-id  | int  | Yes      | ID of the gym         | 123     |

---

## Request Body Parameters
| Name        | Type         | Required | Description                                 | Example                |
|-------------|--------------|----------|---------------------------------------------|------------------------|
| title       | string       | No       | Title of the admin (max 255 characters)     | "Manager"             |
| user_id     | int          | Yes      | ID of the user to grant admin access        | 42                     |
| permissions | int array    | Yes      | Permission **IDs** to grant. Each must exist (`exists:permissions,id`). Only the IDs published by [`GET /gyms/admin-permissions`](delegatable-permissions.md) do anything | [17, 23] |

---

## Request Example
```json
{
  "title": "Manager",
  "user_id": 42,
  "permissions": [17, 23]
}
```

Passing an ID outside the delegatable set is accepted and stored, and grants nothing — `Gym::adminCan()` is
only ever asked about the published names.

---

## Response

### 201 Created
Returns the created gym admin resource.

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
