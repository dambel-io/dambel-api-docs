# `GET /api/v1/admin/brands`

Retrieve a list of brands in alphabetical order.


---

## Permissions
| Permission         | Description         |
|--------------------|---------------------|
| `brands.view_all`  | Access brands       |

---

## Response

### 200 OK
```json
{
  "data": [
    {<brand resource>}, ...
  ]
}
```
- [Brand Resource](brand_resource.md)

---
