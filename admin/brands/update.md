# PUT /api/v1/admin/brands/{brand-id}

Update an existing brand.


---

## Permissions
| Permission         | Description         |
|--------------------|---------------------|
| `brands.view_all`  | Access brands       |
| `brands.update`    | Update a brand      |

---

## Request Body Parameters
| Name          | Type   | Required | Description                      |
|---------------|--------|----------|----------------------------------|
| `title`       | string | No       | Name of the brand (max 255)      |
| `link`        | string | No       | Website link (max 255, optional) |
| `description` | string | No       | Description (optional)           |

*All parameters are optional. If omitted, they will not be updated.*

---

## Response

### 200 OK
Returns the updated brand resource.

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
