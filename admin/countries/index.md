# `GET /api/v1/admin/countries`

Retrieve a list of countries in alphabetical order.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `countries.view_all`  | Access countries    |

---

## Response

### 200 OK
```
{
  "data": [
    {<country resource>}, ...
  ]
}
```
- [Country Resource](country_resource.md)

---
