# Marketing Boost Resource

Represents a marketing boost applied to a resource (e.g., gym, training service), including its type, level, and active period.


---

## Schema
| Field           | Type    | Description                                      | Example                |
|-----------------|---------|--------------------------------------------------|------------------------|
| id              | int     | Unique identifier for the boost                  | 123                    |
| boostable_type  | string  | Type of the boosted resource (e.g., `App\\Models\\Gym`) | "App\\Models\\Gym"      |
| boostable_id    | int     | ID of the boosted resource                       | 123                    |
| level           | int     | Level of the boost                               | 1                      |
| starts_at       | string  | Start timestamp (ISO 8601 format)                | "2025-01-01 00:00:00" |
| ends_at         | string  | End timestamp (ISO 8601 format)                  | "2025-02-01 00:00:00" |

---

## Example
```json
{
  "id": 123,
  "boostable_type": "App\\Models\\Gym",
  "boostable_id": 123,
  "level": 1,
  "starts_at": "2025-01-01 00:00:00",
  "ends_at": "2025-02-01 00:00:00"
}
```
