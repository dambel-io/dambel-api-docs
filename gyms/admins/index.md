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
      "permissions": ["edit_gym", "view"]
    }
  ]
}
```

For a full schema, see [Gym Admin Resource](gym_admin_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../../_globals/not-found-errors.md) |
