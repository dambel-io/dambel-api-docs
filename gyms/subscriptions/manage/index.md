# GET /api/v1/gyms/{gym-id}/subscriptions/manage

Retrieves a list of subscriptions for a specific gym, with filtering and pagination options.


---

## Permissions
| Permission                    | Description                                 |
|-------------------------------|---------------------------------------------|
| `gym_subscriptions.view`      | View subscriptions for your own gyms        |
| `gym_subscriptions.view_any`  | View subscriptions for any gym              |

---

## URL Parameters
| Name    | Type | Required | Description                | Example |
|---------|------|----------|----------------------------|---------|
| gym-id  | int  | Yes      | ID of the gym              | 123     |

---

## Query Parameters
| Name             | Type    | Required | Description                                        | Example         |
|------------------|---------|----------|----------------------------------------------------|-----------------|
| page             | int     | No       | Page number for pagination                         | 1               |
| user_id          | string  | No       | User ID(s), comma-separated                        | "10,20"        |
| gym_plan_id      | string  | No       | Plan ID(s), comma-separated                        | "1,2,3"        |
| expires_at_from  | string  | No       | Filter: subscriptions expiring after this date     | "2025-01-01"   |
| expires_at_to    | string  | No       | Filter: subscriptions expiring before this date    | "2025-12-31"   |

---

## Request Example
```
GET /api/v1/gyms/123/subscriptions/manage?user_id=10&gym_plan_id=1&page=1
Authorization: Bearer {token}
```

---

## Response

### 200 OK
Returns a paginated list of gym subscription resources.

#### Example
```json
{
  "data": [ { /* gym subscription resource */ }, ... ],
  "links": { /* pagination data */ },
  "meta": { /* pagination data */ }
}
```

For a full schema, see [Gym Subscription Resource](../gym_subscription.md) and [Pagination Data](../../../_globals/pagination-data.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 404    | Not found (invalid gym or plan) |  |
| 401    | Unauthorized               | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../../_globals/permission-errors.md) |
