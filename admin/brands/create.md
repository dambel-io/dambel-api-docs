# `POST /api/v1/admin/brands`

Create a new brand.


---

## Permissions
| Permission         | Description         |
|--------------------|---------------------|
| `brands.view_all`  | Access brands       |
| `brands.create`    | Create a brand      |

---

## Request Body Parameters
| Name           | Type    | Required | Description                        |
|----------------|---------|----------|------------------------------------|
| `name`         | string  | Yes      | Name of the brand (max 255)        |
| `link`         | string  | No       | Website link (max 255, optional)   |
| `description`  | string  | No       | Description (optional)             |

---

## Response

### 201 Created
```
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
