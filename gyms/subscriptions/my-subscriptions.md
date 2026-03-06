# GET /api/v1/gyms/my-subscriptions

Retrieves the current user's subscriptions across all gyms.


---

## Request Example
```
GET /api/v1/gyms/my-subscriptions
Authorization: Bearer {token}
```

---

## Response

### 200 OK
Returns a list of the user's gym subscriptions across all active gyms.

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
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
