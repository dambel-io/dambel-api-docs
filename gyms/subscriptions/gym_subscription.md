# Gym Subscription Resource

Represents a user's subscription to a gym plan, including expiration, available sessions, and check-ins.


---

## Schema
| Field                    | Type    | Description                                 | Example                |
|--------------------------|---------|---------------------------------------------|------------------------|
| id                       | int     | Unique identifier for the subscription      | 123                    |
| user_id                  | int     | ID of the user                              | 789                    |
| gym_plan                 | object  | Gym plan resource object                    | { ... }                |
| expires_at               | string  | Expiration date (YYYY-MM-DD)                | "2025-01-01"          |
| available_sessions_count | int     | Number of available sessions                | 16                     |
| checkins                 | array   | List of check-in resources                  | [ { ... }, ... ]       |

---

## Example
```json
{
  "id": 123,
  "user_id": 789,
  "gym_plan": { /* gym plan resource */ },
  "expires_at": "2025-01-01",
  "available_sessions_count": 16,
  "checkins": [ { /* gym subscription checkin resource */ } ]
}
```

For schemas, see [Gym Plan Resource](../plans/gym_plan_resource.md) and [Gym Subscription Check-in Resource](gym_subscription_checkin_resource.md).
