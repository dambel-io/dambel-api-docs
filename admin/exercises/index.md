# `GET /api/v1/admin/exercises`

Retrieve a list of exercises in alphabetical order.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `exercises.view_all`  | Access exercises    |

---

## Response

### 200 OK
```
{
  "data": [
    {<exercise resource>}, ...
  ]
}
```
- [Exercise Resource](exercise_resource.md)

---
