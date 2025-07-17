# PUT /api/v1/gyms/{gym-id}/subscriptions/manage/{subscription-id}

Updates a subscription for a user in a specific gym.


---

## Permissions
| Permission                    | Description                                 |
|-------------------------------|---------------------------------------------|
| `gym_subscriptions.update`    | Update subscriptions for your own gyms      |
| `gym_subscriptions.update_any`| Update subscriptions for any gym            |

---

## URL Parameters
| Name             | Type | Required | Description                | Example |
|------------------|------|----------|----------------------------|---------|
| gym-id           | int  | Yes      | ID of the gym              | 123     |
| subscription-id  | int  | Yes      | ID of the subscription     | 456     |

---

## Request Body Parameters
| Name                   | Type    | Required | Description                                 | Example         |
|------------------------|---------|----------|---------------------------------------------|-----------------|
| expires_at             | string  | No       | Expiration date (YYYY-MM-DD, optional)      | "2025-12-31"   |
| available_sessions_count| int    | No       | Number of available sessions (optional)      | 10              |

All parameters are optional; only include fields you wish to update. You can set them to null to clear their value.

---

## Request Example
```json
{
  "expires_at": "2025-12-31",
  "available_sessions_count": 10
}
```

---

## Response

### 200 OK
Returns the updated gym subscription resource.

#### Example
```json
{ /* gym subscription resource */ }
```

For a full schema, see [Gym Subscription Resource](../gym_subscription.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 404    | Not found (invalid gym or subscription) |  |
| 422    | Validation error           | [Validation error](../../../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../../_globals/permission-errors.md) |
