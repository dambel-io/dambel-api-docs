# PUT /api/v1/admin/roles/{role-id}

Update an existing role.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `roles.view_all`      | Access roles        |
| `roles.update`        | Update role         |

---

## Request Body Parameters
| Name           | Type    | Required | Description                        |
|----------------|---------|----------|------------------------------------|
| `name`         | string  | Yes      | Name of the role (max 255)         |
| `permissions`  | array   | No       | List of permission IDs (optional)  |

---

## Response

### 200 OK
```json
{
  "data": { /* role resource */ }
}
```
- [Role Resource](role_resource.md)

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 422    | Validation error          | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not found                 | [Not found error](../../_globals/not-found-errors.md)           |

---
