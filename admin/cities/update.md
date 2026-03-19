# PUT /api/v1/admin/cities/{city-id}

Update an existing city.


---

## Permissions
| Permission         | Description         |
|--------------------|---------------------|
| `cities.view_all`  | Access cities       |
| `cities.update`    | Update a city       |

---

## Request Body Parameters
| Name     | Type    | Required | Description                        |
|----------|---------|----------|------------------------------------|
| `name`   | string  | Yes      | Name of the city (max 255)         |

---

## Response

### 200 OK
```json
{
  "data": { /* city resource */ }
}
```
- [City Resource](city_resource.md)

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 422    | Validation error          | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |

---
