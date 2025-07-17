# `GET /api/v1/admin/states`

Retrieve a list of states in alphabetical order. Optionally filter by country.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `states.view_all`     | Access states       |

---

## Query Parameters
| Name         | Type    | Required | Description                        |
|--------------|---------|----------|------------------------------------|
| `country_id` | integer | No       | Filter by country ID               |

---

## Response

### 200 OK
```
{
  "data": [
    {<state resource>}, ...
  ]
}
```
- [State Resource](state_resource.md)

---
