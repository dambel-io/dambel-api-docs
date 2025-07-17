# `POST /api/v1/admin/supplements`

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

### 201 Created
```
{
  "supplement": {<supplement resource>}
}
```
- [Supplement Resource](supplement_resource.md)

---

## Error Responses
- **422 Unprocessable Entity:** [Validation error](../../_globals/validation-errors.md)
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)

---
