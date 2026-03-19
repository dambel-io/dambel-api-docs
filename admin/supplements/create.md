# POST /api/v1/admin/supplements

Create a new supplement.


---

## Permissions
| Permission               | Description         |
|--------------------------|---------------------|
| `supplements.view_all`   | Access supplements  |
| `supplements.create`     | Create supplement   |

---

## Request Body Parameters
| Name           | Type    | Required | Description                        |
|----------------|---------|----------|------------------------------------|
| `title`        | string  | Yes      | Name of the supplement (max 255)   |
| `link`         | string  | No       | Wiki link (max 255, optional)      |
| `description`  | string  | No       | Description (optional)             |

---

## Response

### 200 OK
```json
{
  "data": { /* supplement resource */ }
}
```
- [Supplement Resource](supplement_resource.md)

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 422    | Validation error          | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |

---
