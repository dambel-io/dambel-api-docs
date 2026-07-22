# PUT /api/v1/admin/muscle-groups/{muscle-group-id}

Update an existing muscle group.


---

## Permissions
| Permission               | Description          |
|--------------------------|----------------------|
| `muscle_groups.view_all` | Access muscle groups |
| `muscle_groups.update`   | Update muscle group  |

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
| 404    | Not found                 | [Not-found error](../../_globals/not-found-errors.md)           |

---
