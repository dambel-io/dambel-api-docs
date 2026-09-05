# GET /api/v1/gyms/my-subscriptions

Retrieves the current user's subscriptions across all gyms, newest expiry first.


---

## Query Parameters

| Name     | Type | Req | Description                                                        | Example |
|----------|------|-----|--------------------------------------------------------------------|---------|
| per_page | int  | No  | Results per page. Defaults to 50; must be between 1 and 100. A value outside that range is a 422, not a clamp.                    | 20      |
| page     | int  | No  | Page number.                                                        | 2       |

---

## Request Example
```
GET /api/v1/gyms/my-subscriptions?per_page=20
Authorization: Bearer {token}
```

---

## Response

### 200 OK
A paginated list of the user's gym subscriptions across all active gyms.

#### Example
```json
{
  "data": [
    { /* gym subscription resource */ },
    { /* gym subscription resource */ }
  ],
  "links": { "first": "...", "last": "...", "prev": null, "next": "..." },
  "meta": { "current_page": 1, "from": 1, "last_page": 3, "per_page": 50, "to": 50, "total": 120 }
}
```

For a full schema, see [Gym Subscription Resource](gym_subscription.md) and
[Pagination Data](../../_globals/pagination-data.md).

> Subscriptions to inactive gyms are never returned.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 422    | Validation error — `per_page` outside 1–100 | [Validation error](../../_globals/validation-errors.md) |
