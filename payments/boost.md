# POST /api/v1/payments/boost

Boost a resource (e.g., gym or training service) using a selected boost plan.


---

## Permissions
| Permission           | Description                |
|----------------------|----------------------------|
| `payments.boost_own` | Boost your own resources   |
| `payments.boost_all` | Boost any resource         |

---

## Request Body Parameters
| Name           | Type   | Required | Description                                              | Example  |
|----------------|--------|----------|----------------------------------------------------------|----------|
| boostable_type | string | Yes      | Type of resource to boost (`gym` or `training_service`)  | "gym"   |
| boostable_id   | int    | Yes      | ID of the resource to boost                              | 42       |
| plan           | string | Yes      | Name of the boost plan                                   | "basic" |

Use [`/prices`](prices.md) to get available plan names and pricing.

---

## Request Example
```json
{
  "boostable_type": "gym",
  "boostable_id": 42,
  "plan": "basic"
}
```

---

## Response

### 200 OK
Returns the created marketing boost resource.

```json
{
  "data": {
    "id": 101,
    "boostable_type": "App\\Models\\Gym",
    "boostable_id": 42,
    "level": 1,
    "starts_at": "2024-01-01 00:00:00",
    "ends_at": "2024-01-08 00:00:00"
  }
}
```

See [Marketing Boost Resource](marketing_boost_resource.md).

---

### Error Responses
| Status | Description               | Reference                                                    |
|--------|---------------------------|--------------------------------------------------------------|
| 400    | Already have a boost      |                                                              |
| 400    | Insufficient balance      |                                                              |
| 404    | Plan not found            |                                                              |
| 422    | Validation error          | [Validation error](../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../_globals/permission-errors.md)         |
