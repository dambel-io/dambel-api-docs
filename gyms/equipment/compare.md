# GET /api/v1/gyms/{gym-id}/equipment/compare/{workout-plan}

Compare workout plan required equipment to the gym equipment list to get list of the missing equipment in that gym for that workout plan.


---

## Permissions
| Permission      | Description                                             |
|-----------------|---------------------------------------------------------|
| `gyms.view_all` | Required to view equipment for an inactive gym          |
| `workout_plans.view`          | To view your own workout plans |

---

## URL Parameters
| Name    | Type | Required | Description                | Example |
|---------|------|----------|----------------------------|---------|
| gym-id  | int  | Yes      | ID of the gym              | 123     |
| workout-plan-id  | int  | Yes      | ID of the workout plan              | 123     |

---

## Request Example
```
GET /api/v1/gyms/123/equipment/compare/123
Authorization: Bearer {token}
```

---

## Response

### 200 OK
Returns a list of the missing equipment

#### Example
```json
{
  "data": [ { /* equipment resource */ }, ... ]
}
```

For a full schema, see [Equipment Resource](../../admin/equipment/equipment_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../../_globals/not-found-errors.md) |
