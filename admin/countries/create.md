# `POST /api/v1/admin/countries`

Create a new country.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `countries.view_all`  | Access countries    |
| `countries.create`    | Create a country    |

---

## Request Body Parameters
| Name     | Type    | Required | Description                        |
|----------|---------|----------|------------------------------------|
| `name`   | string  | Yes      | Name of the country (max 255)      |

---

## Response

### 201 Created
```
{
  "country": {<country resource>}
}
```
- [Country Resource](country_resource.md)

---

## Error Responses
- **422 Unprocessable Entity:** [Validation error](../../_globals/validation-errors.md)
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)

---
