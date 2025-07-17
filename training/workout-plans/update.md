# `PUT /api/v1/training/workout-plans/{workout-plan-id}`

Update a workout plan.


---

## Permissions
| Permission             | Description                                 |
|------------------------|---------------------------------------------|
| `workout_plans.update` | Update your own or trainee's workout plans  |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                 |
|--------------|---------|----------|---------------------------------------------|
| `title`      | string  | No       | Title of the workout plan (max 255)         |
| `description`| string  | No       | Description (max 2000, optional)            |

*All parameters are optional. If omitted, they will not be updated.*

---

## Response

### 200 OK
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
