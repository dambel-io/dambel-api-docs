# POST /api/v1/admin/brands

Create a new brand.


---

## Permissions
| Permission         | Description         |
|--------------------|---------------------|
| `brands.view_all`  | Access brands       |
| `brands.create`    | Create a brand      |

---

## Request Body Parameters
| Name          | Type   | Required | Description                      |
|---------------|--------|----------|----------------------------------|
| `title`       | string | Yes      | Name of the brand (max 255)      |
| `link`        | string | No       | Website link (max 255, optional) |
| `description` | string | No       | Description (optional)           |

---

## Response

### 200 OK
Returns the created brand resource.

```json
{
  "data": { /* brand resource */ }
}
```

See [Brand Resource](brand_resource.md).

---

## Error Responses
| Status | Description               | Reference                                                    |
|--------|---------------------------|--------------------------------------------------------------|
| 422    | Validation error          | [Validation error](../../_globals/validation-errors.md)      |
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden                 | [Permission error](../../_globals/permission-errors.md)      |
