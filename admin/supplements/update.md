# `PUT /api/v1/admin/supplements/{supplement-id}`

Update an existing supplement.


---

## Permissions
| Permission               | Description         |
|--------------------------|---------------------|
| `supplements.view_all`   | Access supplements  |
| `supplements.update`     | Update supplement   |

---

## Request Body Parameters
| Name           | Type    | Required | Description                        |
|----------------|---------|----------|------------------------------------|
| `title`        | string  | No       | Name of the supplement (max 255)   |
| `link`         | string  | No       | Wiki link (max 255, optional)      |
| `description`  | string  | No       | Description (optional)             |

*All parameters are optional. If omitted, they will not be updated.*

---

## Response

### 200 OK
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
