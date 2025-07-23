# `GET /api/v1/admin/cities`

Retrieve a list of cities in alphabetical order. Optionally filter by state.


---

## Permissions
| Permission         | Description         |
|--------------------|---------------------|
| `cities.view_all`  | Access cities       |

---

## Query Parameters
| Name        | Type    | Required | Description                        |
|-------------|---------|----------|------------------------------------|
| `state_id`  | integer | No       | Filter by state ID                 |

---

## Response

### 200 OK
```json
{
  "data": [
    {<city resource>}, ...
  ]
}
```
- [City Resource](city_resource.md)

---
