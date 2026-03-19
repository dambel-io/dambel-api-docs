# POST /api/v1/admin/countries

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

### 200 OK
```json
{
  "data": { /* country resource */ }
}
```
- [Country Resource](country_resource.md)

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 422    | Validation error          | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |

---
