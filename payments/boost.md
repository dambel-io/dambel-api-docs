# POST /api/v1/payments/boost

Boost a resource (e.g., gym or training service) using a selected boost plan.


---

## Permissions
| Permission           | Description                        |
|----------------------|------------------------------------|
| `payments.boost_own` | Boost your own resources           |
| `payments.boost_all` | Boost any resource                 |

---

## Request Body Parameters
| Name           | Type   | Required | Description                                 | Example           |
|----------------|--------|----------|---------------------------------------------|-------------------|
| boostable_type | string | Yes      | Type of resource to boost (`gym`, `training_service`) | "gym"            |
| boostable_id   | int    | Yes      | ID of the resource to boost                 | 42                |
| plan           | string | Yes      | Name of the boost plan                      | "premium"        |

Use [`/prices`](prices.md) to get available plans and prices.

---

## Request Example
```json
{
  "boostable_type": "gym",
  "boostable_id": 42,
  "plan": "premium"
}
```

---

## Response

### 201 Created
Returns the created marketing boost resource.

#### Example
```json
{
  "id": 101,
  "boostable_type": "App\\Models\\Gym",
  "boostable_id": 42,
  "plan": "premium",
  "status": "active",
  "starts_at": "2024-01-01T00:00:00Z",
  "ends_at": "2024-01-31T23:59:59Z"
}
```

For a full schema, see [Marketing Boost Resource](marketing_boost_resource.md).

---

### Error Responses
| Status | Description                | Example/Reference                                      |
|--------|----------------------------|--------------------------------------------------------|
| 400    | Already have a boost       | `{ "error": "You already have a boost" }`            |
| 400    | Insufficient balance       | `{ "error": "Insufficient balance" }`                |
| 404    | Plan not found             | `{ "error": "Plan not found" }`                      |
| 422    | Validation error           | [Validation error](../_globals/validation-errors.md)    |
| 500    | Purchase failed            | `{ "error": "Purchase failed" }`                     |
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md)    |
