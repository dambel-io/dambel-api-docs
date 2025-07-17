# `POST /api/v1/admin/states/{country}`

Create a new state in a given country.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `states.view_all`     | Access states       |
| `states.create`       | Create state        |

---

## Request Body Parameters
| Name     | Type    | Required | Description                        |
|----------|---------|----------|------------------------------------|
| `name`   | string  | Yes      | Name of the state (max 255)        |

*The country ID is provided in the route.*

---

## Response

### 201 Created
```
{
  "state": {<state resource>}
}
```
- [State Resource](state_resource.md)

---

## Error Responses
- **422 Unprocessable Entity:** [Validation error](../../_globals/validation-errors.md)
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)

---
