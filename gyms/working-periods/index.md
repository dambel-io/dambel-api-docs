# GET /api/v1/gyms/{gym-id}/working-periods

Retrieves a list of working periods for a specific gym.


---

## Permissions
| Permission      | Description                                             |
|-----------------|---------------------------------------------------------|
| `gyms.view_all` | Required to view working periods for an inactive gym    |

---

## URL Parameters
| Name    | Type | Required | Description                | Example |
|---------|------|----------|----------------------------|---------|
| gym-id  | int  | Yes      | ID of the gym              | 123     |

---

## Request Example
```
GET /api/v1/gyms/123/working-periods
Authorization: Bearer {token}
```

---

## Response

### 200 OK
Returns a list of working period resources, sorted by weekday and opening time.

#### Example
```json
{
  "data": [ { /* working period resource */ }, ... ]
}
```

For a full schema, see [Working Period Resource](gym_working_period_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../../_globals/not-found-errors.md) |
