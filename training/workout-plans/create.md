# POST /api/v1/training/workout-plans

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
| `is_active`| boolean  | No       | Set as active plan (optional, default false). It changes all other plans to false if is set to true            |
| `trainee_id` | int     | No       | Trainee ID (if creating for a trainee)      |

> Note: Current active plan will automatically get deactivated if you set `is_active` to true.

---

## Response

### 201 Created
```json
{ /* workout plan resource */ }
```
- [Workout Plan Resource](workout_plan_resource.md)

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 422    | Validation error          | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |

---
