# `/api/v1/training/diet-plans`

Create a new diet plan.


---

## Permissions
| Permission        | Description                                 |
|-------------------|---------------------------------------------|
| `diet_plans.create` | Create diet plan for yourself or a trainee |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                 |
|--------------|---------|----------|---------------------------------------------|
| `title`      | string  | Yes      | Title of the diet plan (max 255)            |
| `description`| string  | No       | Description (max 2000, optional)            |
| `is_active`| boolean  | No       | Set as active plan (optional, default false). It changes all other plans to false if is set to true            |
| `target_daily_water`| float  | No       | Suggest the daily water consumption in liters            |
| `trainee_id` | int     | No       | Trainee ID (if creating for a trainee)      |

> Note: Current active plan will automatically get deactivated if you set `is_active` to true.

---

## Response

### 201 Created
```
<diet plan resource>
```
- See [Diet Plan Resource](diet_plan_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 422    | Validation Error   | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
