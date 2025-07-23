# `GET /api/v1/admin/equipment`

Retrieve a list of equipment in alphabetical order.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `equipment.view_all`  | Access equipment    |

---

## Response

### 200 OK
```json
{
  "data": [
    {<equipment resource>}, ...
  ]
}
```
- [Equipment Resource](equipment_resource.md)

---
