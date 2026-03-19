# POST /api/v1/admin/equipment

Create a new equipment item.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `equipment.view_all`  | Access equipment    |
| `equipment.create`    | Create equipment    |

---

## Request Body Parameters
| Name           | Type    | Required | Description                        |
|----------------|---------|----------|------------------------------------|
| `name`         | string  | Yes      | Name of the equipment (max 255)    |
| `link`         | string  | No       | Tutorial link (max 255, optional)  |
| `description`  | string  | No       | Description (optional)             |

---

## Response

### 200 OK
```json
{
  "data": { /* equipment resource */ }
}
```
- [Equipment Resource](equipment_resource.md)

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 422    | Validation error          | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |

---
