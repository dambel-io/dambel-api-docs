# `GET /api/v1/admin/majors`

Retrieve a list of majors.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `majors.view_all`     | Access majors       |

---

## Response

### 200 OK
```json
{
  "data": [
    {<major resource>}, ...
  ]
}
```
- [Major Resource](major_resource.md)

---
