# `PUT /api/v1/admin/brands/{brand-id}`

Update an existing brand.


---

## Permissions
| Permission         | Description         |
|--------------------|---------------------|
| `brands.view_all`  | Access brands       |
| `brands.update`    | Update a brand      |

---

## Request Body Parameters
| Name           | Type    | Required | Description                        |
|----------------|---------|----------|------------------------------------|
| `name`         | string  | No       | Name of the brand (max 255)        |
| `link`         | string  | No       | Website link (max 255, optional)   |
| `description`  | string  | No       | Description (optional)             |

*All parameters are optional. If omitted, they will not be updated.*

---

## Response

### 200 OK
```json
{
  "brand": {<brand resource>}
}
```
- [Brand Resource](brand_resource.md)

---

## Error Responses
- **422 Unprocessable Entity:** [Validation error](../../_globals/validation-errors.md)
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)

---
