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
| permissions | string array | Yes      | List of permission names for the admin      | ["edit_gym", "view"]  |

---

## Request Example
```json
{
  "title": "Manager",
  "user_id": 42,
  "permissions": ["edit_gym", "view"]
}
```

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
  "permissions": ["edit_gym", "view"]
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
