# `POST /api/v1/admin/majors`

Create a new major.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `majors.view_all`     | Access majors       |
| `majors.create`       | Create major        |

---

## Request Body Parameters
| Name     | Type    | Required | Description                        |
|----------|---------|----------|------------------------------------|
| `title`  | string  | Yes      | Name of the major (max 255)        |

---

## Response

### 201 Created
```
{
  "major": {<major resource>}
}
```
- [Major Resource](major_resource.md)

---

## Error Responses
- **422 Unprocessable Entity:** [Validation error](../../_globals/validation-errors.md)
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)

---
