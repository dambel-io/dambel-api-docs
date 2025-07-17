# POST /api/v1/gyms/{gym-id}/plans

Creates a new subscription plan for a gym.


---

## Permissions
| Permission                | Description                                 |
|---------------------------|---------------------------------------------|
| `gym_plans.create`        | Create plans for your own gyms              |
| `gym_plans.create_any`    | Create plans for any gym                    |

---

## URL Parameters
| Name    | Type | Required | Description                | Example |
|---------|------|----------|----------------------------|---------|
| gym-id  | int  | Yes      | ID of the gym              | 123     |

---

## Request Body Parameters
| Name           | Type    | Required | Description                                 | Example         |
|----------------|---------|----------|---------------------------------------------|-----------------|
| title          | string  | Yes      | Title of the plan (max 255 chars)           | "Basic"        |
| description    | string  | No       | Description (max 2000 chars, optional)      | "Some desc"    |
| price          | int     | Yes      | Price of the plan                           | 150000          |
| discount       | float   | No       | Discount percentage (optional, default 0)   | 10.0            |
| duration_days  | int     | No       | Number of days until expiration (optional)  | 30              |
| sessions_count | int     | No       | Number of sessions in the plan (optional)   | 20              |
| is_active      | bool    | No       | Whether the plan is active                  | true            |

**Note:** Either `duration_days` or `sessions_count` can be null.

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

### 201 Created
Returns the created gym plan resource.

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
