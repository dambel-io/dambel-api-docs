# PUT /api/v1/training/workout-plans/{workout-plan-id}

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
| `is_active`| boolean  | No       | Set as active plan (optional, default false). It changes all other plans to false if is set to true            |

*All parameters are optional. If omitted, they will not be updated.*

> Note: Current active plan will automatically get deactivated if you set `is_active` to true.

---

## Response

### 200 OK
```json
{
  "data": { /* workout plan resource */ }
}
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
