# `PUT /api/v1/admin/equipment/{equipment-id}`

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

*All parameters are optional. If omitted, they will not be updated.*

---

## Response

### 200 OK
```
{
  "equipment": {<equipment resource>}
}
```
- [Equipment Resource](equipment_resource.md)

---

## Error Responses
- **422 Unprocessable Entity:** [Validation error](../../_globals/validation-errors.md)
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)

---
