# GET /api/v1/gyms/{gym-id}/subscriptions/{subscription-id}/checkins

Retrieves a paginated list of a subscription's check-ins, newest first. This is the replacement for the
deprecated `checkins` array nested inside the [Gym Subscription Resource](../gym_subscription.md).


---

## Permissions
The subscriber themselves always has access. A gym admin needs:

| Permission                    | Description                                 |
|-------------------------------|---------------------------------------------|
| `gym_subscriptions.view`      | View subscriptions of a gym you administer  |
| `gym_subscriptions.view_any`  | View subscriptions of any gym               |

---

## URL Parameters
| Name             | Type | Required | Description                     | Example |
|------------------|------|----------|---------------------------------|---------|
| gym-id           | int  | Yes      | ID of the gym                   | 123     |
| subscription-id  | int  | Yes      | ID of the gym subscription      | 456     |

---

## Query Parameters
| Name     | Type | Required | Description                                      | Example |
|----------|------|----------|--------------------------------------------------|---------|
| per_page | int  | No       | Results per page. Defaults to 50; must be between 1 and 100. A value outside that range is a 422, not a clamp. | 20      |
| page     | int  | No       | Page number.                                     | 2       |

---

## Request Example
```
GET /api/v1/gyms/123/subscriptions/456/checkins?per_page=20
Authorization: Bearer {token}
```

---

## Response

### 200 OK
A paginated list of the subscription's check-ins, ordered by `checked_in_at` descending.

#### Example
```json
{
  "data": [
    { /* gym subscription check-in resource */ },
    { /* gym subscription check-in resource */ }
  ],
  "links": { "first": "...", "last": "...", "prev": null, "next": "..." },
  "meta": { "current_page": 1, "from": 1, "last_page": 3, "per_page": 50, "to": 50, "total": 120 }
}
```

For a full schema, see [Gym Subscription Check-in Resource](../gym_subscription_checkin_resource.md) and
[Pagination Data](../../../_globals/pagination-data.md).

---

### Error Responses
| Status | Description                                              | Reference                                      |
|--------|----------------------------------------------------------|------------------------------------------------|
| 401    | Unauthorized                                             | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden — not the subscriber and not a gym admin       | [Permission error](../../../_globals/permission-errors.md) |
| 404    | The subscription does not belong to the gym in the path  |  |
| 422    | Validation error — `per_page` outside 1–100              | [Validation error](../../../_globals/validation-errors.md) |
