# `/api/v1/training/diet-plans/{diet-plan-id}`

Update a diet plan.


---

## Permissions
| Permission        | Description                                 |
|-------------------|---------------------------------------------|
| `diet_plans.update` | Update your own or trainee's diet plans    |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                 |
|--------------|---------|----------|---------------------------------------------|
| `title`      | string  | No       | Title of the diet plan (max 255)            |
| `description`| string  | No       | Description (max 2000, optional)            |
| `is_active`| boolean  | No       | Set as active plan (optional, default false). It changes all other plans to false if is set to true            |

*All parameters are optional. If omitted, they will not be updated. You can set them to null if desired.*

> Note: Current active plan will automatically get deactivated if you set `is_active` to true.

---

## Response

### 200 OK
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
