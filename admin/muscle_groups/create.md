# POST /api/v1/admin/muscle-groups

Create a new muscle group.


---

## Permissions
| Permission               | Description          |
|--------------------------|----------------------|
| `muscle_groups.view_all` | Access muscle groups |
| `muscle_groups.create`   | Create muscle group  |

---

## Request Body Parameters
| Name     | Type    | Required | Description                          |
|----------|---------|----------|--------------------------------------|
| `title`  | string  | Yes      | Name of the muscle group (max 255)   |

---

## Response

### 200 OK
```json
{
  "data": { /* muscle group resource */ }
}
```
- [Muscle Group Resource](muscle_group_resource.md)

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 422    | Validation error          | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |

---
