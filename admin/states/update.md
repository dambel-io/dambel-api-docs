# PUT /api/v1/admin/states/{state-id}

Update an existing state.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `states.view_all`     | Access states       |
| `states.update`       | Update state        |

---

## Request Body Parameters
| Name     | Type    | Required | Description                        |
|----------|---------|----------|------------------------------------|
| `name`   | string  | Yes      | Name of the state (max 255)        |

---

## Response

### 200 OK
```json
{
  "data": { /* state resource */ }
}
```
- [State Resource](state_resource.md)

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 422    | Validation error          | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |

---
