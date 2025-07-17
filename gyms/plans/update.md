# PUT /api/v1/gyms/{gym-id}/plans/{plan-id}

Updates a specific subscription plan for a gym.


---

## Permissions
| Permission                | Description                                 |
|---------------------------|---------------------------------------------|
| `gym_plans.update`        | Update plans for your own gyms              |
| `gym_plans.update_any`    | Update plans for any gym                    |

---

## URL Parameters
| Name     | Type | Required | Description                | Example |
|----------|------|----------|----------------------------|---------|
| gym-id   | int  | Yes      | ID of the gym              | 123     |
| plan-id  | int  | Yes      | ID of the plan             | 55      |

---

## Request Body Parameters
| Name           | Type    | Required | Description                                 | Example         |
|----------------|---------|----------|---------------------------------------------|-----------------|
| title          | string  | No       | Title of the plan (max 255 chars)           | "Basic"        |
| description    | string  | No       | Description (max 2000 chars, optional)      | "Some desc"    |
| price          | int     | No       | Price of the plan                           | 150000          |
| discount       | float   | No       | Discount percentage (optional, default 0)   | 10.0            |
| duration_days  | int     | No       | Number of days until expiration (optional)  | 30              |
| sessions_count | int     | No       | Number of sessions in the plan (optional)   | 20              |
| is_active      | bool    | No       | Whether the plan is active                  | true            |

**Note:** Either `duration_days` or `sessions_count` can be null. All parameters are optional; only include fields you wish to update. You can set them to null to clear their value.

---

## Request Example
```json
{
  "title": "Basic",
  "description": "Some desc",
  "price": 150000,
  "discount": 10.0,
  "duration_days": 30,
  "sessions_count": 20,
  "is_active": true
}
```

---

## Response

### 200 OK
Returns the updated gym plan resource.

#### Example
```json
{ /* gym plan resource */ }
```

For a full schema, see [Gym Plan Resource](gym_plan_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 422    | Validation error           | [Validation error](../../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
