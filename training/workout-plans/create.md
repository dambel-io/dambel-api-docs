# `POST /api/v1/training/workout-plans`

Create a new workout plan for yourself or a trainee.


---

## Permissions
| Permission             | Description                                 |
|------------------------|---------------------------------------------|
| `workout_plans.create` | Create workout plan for yourself or trainee |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                 |
|--------------|---------|----------|---------------------------------------------|
| `title`      | string  | Yes      | Title of the workout plan (max 255)         |
| `description`| string  | No       | Description (max 2000, optional)            |
| `trainee_id` | int     | No       | Trainee ID (if creating for a trainee)      |

---

## Response

### 201 Created
```
<workout plan resource>
```
- [Workout Plan Resource](workout_plan_resource.md)

---

## Error Responses
- **422 Unprocessable Entity:** [Validation error](../../_globals/validation-errors.md)
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)

---
