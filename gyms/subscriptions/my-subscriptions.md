# GET /api/v1/gyms/{gym-id}/subscriptions/my-subscriptions

Retrieves the current user's subscriptions for a specific gym.


---

## URL Parameters
| Name    | Type | Required | Description                | Example |
|---------|------|----------|----------------------------|---------|
| gym-id  | int  | Yes      | ID of the gym              | 123     |

---

## Request Example
```
GET /api/v1/gyms/123/subscriptions/my-subscriptions
Authorization: Bearer {token}
```

---

## Response

### 200 OK
Returns a list of the user's gym subscriptions.

#### Example
```json
[
  { /* gym subscription resource */ },
  { /* gym subscription resource */ }
]
```

For a full schema, see [Gym Subscription Resource](gym_subscription.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 404    | Gym not found              | [Not-found error](../../_globals/not-found-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
