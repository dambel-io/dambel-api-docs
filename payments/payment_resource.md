# Payment Resource

Represents a payment transaction, including its type, amount, status, and associations.


---

## Schema
| Field         | Type    | Description                                      | Example                |
|---------------|---------|--------------------------------------------------|------------------------|
| id            | int     | Unique identifier for the payment                | 123                    |
| user_id       | int     | ID of the user who made the payment              | 123                    |
| type          | string  | Type of payment (see below)                      | "deposit"             |
| amount        | number  | Amount of the payment                            | 100.0                  |
| description   | string  | Description of the payment                       | "Subscription fee"     |
| payable_type  | string  | Type of the payable resource (e.g., `App\Models\Gym`) | "App\\Models\\Gym"      |
| payable_id    | int     | ID of the payable resource                       | 456                    |
| meta          | object  | Additional metadata (if any)                     | { ... }                |
| is_done       | bool    | Whether the payment is completed                 | true                   |
| created_at    | string  | Creation timestamp (ISO 8601 format)             | "2025-01-01 00:00:00" |
| user          | object  | Full user object (see [User Resource](../users/user_resource.md))              | { ... }                |

---

### Type
The `type` field can be one of the following:
- `deposit`
- `income`
- `purchase`
- `withdrawal`
- `commission`

---

## Example
```json
{
  "id": 123,
  "user_id": 123,
  "user": {
    "id": 123,
    "username": "jdoe",
    "first_name": "John",
    "last_name": "Doe",
    "created_at": "2025-01-01 00:00:00"
  },
  "type": "deposit",
  "amount": 100.0,
  "description": "Subscription fee",
  "payable_type": "App\\Models\\Gym",
  "payable_id": 456,
  "meta": {},
  "is_done": true,
  "created_at": "2025-01-01 00:00:00"
}
```
