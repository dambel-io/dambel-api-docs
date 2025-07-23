# `PUT /api/v1/admin/exercises/{exercise-id}`

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

*All parameters are optional. If omitted, they will not be updated.*

---

## Response

### 200 OK
```json
{
  "exercise": {<exercise resource>}
}
```
- [Exercise Resource](exercise_resource.md)

---

## Error Responses
- **422 Unprocessable Entity:** [Validation error](../../_globals/validation-errors.md)
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)

---
