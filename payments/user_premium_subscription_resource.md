# User Premium Subscription Resource

Represents a user's premium subscription, including plan details and validity period.


---

## Schema
| Field       | Type    | Description                                      | Example                |
|-------------|---------|--------------------------------------------------|------------------------|
| id          | int     | Unique identifier for the subscription           | 123                    |
| user_id     | int     | ID of the user                                   | 123                    |
| plan        | string  | Name of the premium plan                         | "gold"                |
| starts_at   | string  | Subscription start timestamp (ISO 8601 format)   | "2025-01-01 00:00:00" |
| expires_at  | string  | Subscription expiry timestamp (ISO 8601 format)  | "2025-02-01 00:00:00" |

---

## Example
```json
{
  "id": 123,
  "user_id": 123,
  "plan": "gold",
  "starts_at": "2025-01-01 00:00:00",
  "expires_at": "2025-02-01 00:00:00"
}
```
