# `PUT /api/v1/admin/majors/{major-id}`

Update an existing major.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `majors.view_all`     | Access majors       |
| `majors.update`       | Update major        |

---

## Request Body Parameters
| Name     | Type    | Required | Description                        |
|----------|---------|----------|------------------------------------|
| `title`  | string  | Yes      | Name of the major (max 255)        |

---

## Response

### 200 OK
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
