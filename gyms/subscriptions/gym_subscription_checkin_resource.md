# Gym Subscription Check-in Resource

Represents a check-in record for a gym subscription, including timestamps and approval status.


---

## Schema
| Field                | Type    | Description                                 | Example                |
|----------------------|---------|---------------------------------------------|------------------------|
| id                   | int     | Unique identifier for the check-in          | 123                    |
| gym_subscription_id  | int     | ID of the gym subscription                  | 456                    |
| checked_in_at        | string  | Check-in timestamp (ISO 8601)               | "2025-01-01 00:00:00" |
| checked_out_at       | string  | Check-out timestamp (ISO 8601, nullable)    | "2025-01-01 03:00:00" |
| user_approved        | bool    | Whether the user approved the check-in      | true                   |
| gym_approved         | bool    | Whether the gym approved the check-in       | false                  |
| notes                | string  | Notes for the check-in (nullable)           | "some notes"          |

---

## Example
```json
{
  "id": 123,
  "gym_subscription_id": 456,
  "checked_in_at": "2025-01-01 00:00:00",
  "checked_out_at": "2025-01-01 03:00:00",
  "user_approved": true,
  "gym_approved": false,
  "notes": "some notes"
}
```
