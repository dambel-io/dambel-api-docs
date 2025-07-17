# POST /api/v1/gyms/{gym-id}/subscriptions/checkin/{subscription-id}

Creates a check-in record for a gym subscription.


---

## Permissions
| Permission                    | Description                                 |
|-------------------------------|---------------------------------------------|
| `gym_subscriptions.checkin`   | Gym admin can check in a user               |

---

## URL Parameters
| Name            | Type | Required | Description                | Example |
|-----------------|------|----------|----------------------------|---------|
| gym-id          | int  | Yes      | ID of the gym              | 123     |
| subscription-id | int  | Yes      | ID of the subscription     | 456     |

---

## Request Body Parameters
| Name  | Type   | Required | Description                | Example      |
|-------|--------|----------|----------------------------|--------------|
| notes | string | No       | Optional note for check-in | "Arrived late" |

---

## Request Example
```json
{
  "notes": "Arrived late"
}
```

---

## Response

### 201 Created
Returns the created check-in resource.

#### Example
```json
{ /* gym subscription check-in resource */ }
```

For a full schema, see [Gym Subscription Check-in Resource](gym_subscription_checkin_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 404    | Not found (invalid gym or subscription, or inactive) |  |
| 400    | Already open check-in exists |  |
| 403    | Forbidden (no permission or gym inactive) | [Permission error](../../_globals/permission-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 422    | Validation error           | [Validation error](../../_globals/validation-errors.md) |
