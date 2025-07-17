# Gym Plan Resource

Represents a subscription plan offered by a gym, including pricing, duration, and status.


---

## Schema
| Field            | Type    | Description                                 | Example      |
|------------------|---------|---------------------------------------------|--------------|
| id               | int     | Unique identifier for the plan              | 123          |
| gym_id           | int     | ID of the gym                               | 123          |
| title            | string  | Title of the plan                           | "Basic"     |
| description      | string  | Description of the plan                     | "Some desc" |
| price            | int     | Price of the plan                           | 150000       |
| discount         | float   | Discount percentage                         | 0            |
| discounted_price | int     | Price after discount                        | 150000       |
| duration_days    | int     | Number of days until expiration (nullable)  | 30           |
| sessions_count   | int     | Number of sessions in the plan (nullable)   | 20           |
| is_active        | bool    | Whether the plan is active                  | true         |

---

## Example
```json
{
  "id": 123,
  "gym_id": 123,
  "title": "Basic",
  "description": "Some desc",
  "price": 150000,
  "discount": 0,
  "discounted_price": 150000,
  "duration_days": 30,
  "sessions_count": 20,
  "is_active": true
}
```
