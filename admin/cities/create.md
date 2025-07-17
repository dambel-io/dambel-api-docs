# `POST /api/v1/admin/cities/{state}`

Create a new city in a given state.


---

## Permissions
| Permission         | Description         |
|--------------------|---------------------|
| `cities.view_all`  | Access cities       |
| `cities.create`    | Create a city       |

---

## Request Body Parameters
| Name     | Type    | Required | Description                        |
|----------|---------|----------|------------------------------------|
| `name`   | string  | Yes      | Name of the city (max 255)         |

*The state ID is provided in the route.*

---

## Response

### 201 Created
```
{
  "city": {<city resource>}
}
```
- [City Resource](city_resource.md)

---

## Error Responses
- **422 Unprocessable Entity:** [Validation error](../../_globals/validation-errors.md)
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)

---
