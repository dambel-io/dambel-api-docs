# `POST /api/v1/admin/exercises`

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
| `link`         | string  | No       | Tutorial link (max 255, optional)  |
| `description`  | string  | No       | Description (optional)             |

---

## Response

### 201 Created
```
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
