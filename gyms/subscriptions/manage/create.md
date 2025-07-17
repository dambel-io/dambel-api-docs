# POST /api/v1/gyms/{gym-id}/subscriptions/manage

Creates a new subscription for a user in a specific gym.


---

## Permissions
| Permission                    | Description                                 |
|-------------------------------|---------------------------------------------|
| `gym_subscriptions.create`    | Create subscriptions for your own gyms      |
| `gym_subscriptions.create_any`| Create subscriptions for any gym            |

---

## URL Parameters
| Name    | Type | Required | Description                | Example |
|---------|------|----------|----------------------------|---------|
| gym-id  | int  | Yes      | ID of the gym              | 123     |

---

## Request Body Parameters
| Name        | Type | Required | Description                | Example |
|-------------|------|----------|----------------------------|---------|
| gym_plan_id | int  | Yes      | ID of the gym plan         | 10      |
| user_id     | int  | Yes      | ID of the user             | 789     |

---

## Request Example
```json
{
  "gym_plan_id": 10,
  "user_id": 789
}
```

---

## Response

### 201 Created
Returns the created gym subscription resource.

#### Example
```json
{ /* gym subscription resource */ }
```

For a full schema, see [Gym Subscription Resource](../gym_subscription.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 404    | Not found (invalid gym or plan) |  |
| 422    | Validation error           | [Validation error](../../../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../../_globals/permission-errors.md) |
