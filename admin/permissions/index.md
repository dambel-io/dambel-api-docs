# `GET /api/v1/admin/permissions`

Retrieve a list of permissions.


---

## Permissions
| Permission               | Description         |
|--------------------------|---------------------|
| `permissions.view_any`   | Access permissions  |

---

## Response

### 200 OK
```
{
  "data": [
    {<permission resource>}, ...
  ]
}
```
- [Permission Resource](permission_resource.md)

---
