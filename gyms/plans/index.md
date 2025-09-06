# GET /api/v1/gyms/{gym-id}/plans

Retrieves a list of subscription plans for a specific gym.


**No authentication required.**

---

## Permissions
| Permission      | Description                                             |
|-----------------|---------------------------------------------------------|
| `gyms.view_all` | Required to view plans for an inactive gym or inactive plans |

---

## URL Parameters
| Name    | Type | Required | Description                | Example |
|---------|------|----------|----------------------------|---------|
| gym-id  | int  | Yes      | ID of the gym              | 123     |

---

## Request Example
```
GET /api/v1/gyms/123/plans
Authorization: Bearer {token}
```

---

## Response

### 200 OK
Returns a list of gym plan resources.

#### Example
```json
{
  "data": [ { /* gym plan resource */ }, ... ]
}
```

For a full schema, see [Gym Plan Resource](gym_plan_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../../_globals/not-found-errors.md) |
