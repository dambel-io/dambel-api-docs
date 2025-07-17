# POST /api/v1/gyms/{gym-id}/subscriptions/subscribe/{plan-id}

Subscribes the user to a gym plan.


---

## URL Parameters
| Name     | Type | Required | Description                | Example |
|----------|------|----------|----------------------------|---------|
| gym-id   | int  | Yes      | ID of the gym              | 123     |
| plan-id  | int  | Yes      | ID of the gym plan         | 10      |

---

## Request Example
```
POST /api/v1/gyms/123/subscriptions/subscribe/10
Authorization: Bearer {token}
```

---

## Response

### 201 Created
Returns the created gym subscription resource.

#### Example
```json
{ /* gym subscription resource */ }
```

For a full schema, see [Gym Subscription Resource](gym_subscription.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 400    | Insufficient account balance|  |
| 404    | Not found (invalid gym or plan, or inactive) |  |
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
