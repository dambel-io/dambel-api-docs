# `GET /api/v1/admin/roles`

Retrieve a list of roles.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `roles.view_all`      | Access roles        |

---

## Response

### 200 OK
```
{
  "data": [
    {<role resource>}, ...
  ]
}
```
- [Role Resource](role_resource.md)

---
