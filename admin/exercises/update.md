# PUT /api/v1/admin/exercises/{exercise-id}

Update an existing exercise.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `exercises.view_all`  | Access exercises    |
| `exercises.update`    | Update exercise     |

---

## Request Body Parameters
| Name           | Type    | Required | Description                        |
|----------------|---------|----------|------------------------------------|
| `name`         | string  | No       | Name of the exercise (max 255)     |
| `link`         | string  | No       | Tutorial link (max 255, optional)  |
| `description`  | string  | No       | Description (optional)             |
| `major_ids`    | string  | No       | Comma-separated list of major IDs. Use `0` to detach all majors. |
| `equipment_ids`| string  | No       | Comma-separated list of equipment IDs. Use `0` to detach all equipment. |

*All parameters are optional. If omitted, they will not be updated.*

---

## Response

### 200 OK
```json
{
  "data": { /* exercise resource */ }
}
```
- [Exercise Resource](exercise_resource.md)

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 422    | Validation error          | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |

---
