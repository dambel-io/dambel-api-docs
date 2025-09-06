# GET /api/v1/gyms/{gym-id}/equipment

Retrieves a list of equipment assigned to a specific gym.


**No authentication required.**

---

## Permissions
| Permission      | Description                                             |
|-----------------|---------------------------------------------------------|
| `gyms.view_all` | Required to view equipment for an inactive gym          |

---

## URL Parameters
| Name    | Type | Required | Description                | Example |
|---------|------|----------|----------------------------|---------|
| gym-id  | int  | Yes      | ID of the gym              | 123     |

---

## Request Example
```
GET /api/v1/gyms/123/equipment
Authorization: Bearer {token}
```

---

## Response

### 200 OK
Returns a list of gym equipment resources.

#### Example
```json
{
  "data": [ { /* gym equipment resource */ }, ... ]
}
```

For a full schema, see [Gym Equipment Resource](gym_equipment_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../../_globals/not-found-errors.md) |
