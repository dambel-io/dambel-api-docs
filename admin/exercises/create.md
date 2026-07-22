# POST /api/v1/admin/exercises

Create a new exercise.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `exercises.view_all`  | Access exercises    |
| `exercises.create`    | Create exercise     |

---

## Request Body Parameters
| Name           | Type    | Required | Description                        |
|----------------|---------|----------|------------------------------------|
| `name`         | string  | Yes      | Name of the exercise (max 255)     |
| `link`         | string  | No       | Exercise GIF filename (max 255, optional) |
| `description`  | string  | No       | Description (optional)             |
| `category`     | string  | No       | Body-part category (max 255, optional) |

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
