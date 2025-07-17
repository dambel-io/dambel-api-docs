# `GET /api/v1/admin/supplements`

Retrieve a list of supplements.


---

## Permissions
| Permission               | Description         |
|--------------------------|---------------------|
| `supplements.view_all`   | Access supplements  |

---

## Response

### 200 OK
```
{
  "data": [
    {<supplement resource>}, ...
  ]
}
```
- [Supplement Resource](supplement_resource.md)

---
