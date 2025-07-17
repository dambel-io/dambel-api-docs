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
| permissions | string array | No       | List of permission names for the admin      | ["edit_gym", "view"]  |

---

## Request Example
```json
{
  "title": "Manager",
  "permissions": ["edit_gym", "view"]
}
```

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
