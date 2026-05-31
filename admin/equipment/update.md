# PUT /api/v1/admin/equipment/{equipment-id}

Update an existing equipment item.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `equipment.view_all`  | Access equipment    |
| `equipment.update`    | Update equipment    |

---

## Request Body Parameters
| Name           | Type    | Required | Description                        |
|----------------|---------|----------|------------------------------------|
| `name`         | string  | No       | Name of the equipment (max 255)    |
| `link`         | string  | No       | Tutorial link (max 255, optional)  |
| `description`  | string  | No       | Description (optional)             |
| `brand_ids`    | string  | No       | Comma-separated list of brand IDs. Use `0` to detach all brands. |
| `major_ids`    | string  | No       | Comma-separated list of major IDs. Use `0` to detach all majors. |
| `exercise_ids` | string  | No       | Comma-separated list of exercise IDs. Use `0` to detach all exercises. |

*All parameters are optional. If omitted, they will not be updated.*

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
