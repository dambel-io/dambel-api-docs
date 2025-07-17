# POST /api/v1/gyms/{gym-id}/equipment

Creates a new equipment entry for a gym.


---

## Permissions
| Permission                | Description                                 |
|---------------------------|---------------------------------------------|
| `gym_equipment.create`    | Create equipment for your own gyms          |
| `gym_equipment.create_any`| Create equipment for any gym                |

---

## URL Parameters
| Name    | Type | Required | Description                | Example |
|---------|------|----------|----------------------------|---------|
| gym-id  | int  | Yes      | ID of the gym              | 123     |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                 | Example |
|--------------|---------|----------|---------------------------------------------|---------|
| equipment_id | int     | Yes      | ID of the equipment                         | 10      |
| count        | int     | Yes      | Number of this equipment in the gym         | 5       |
| brand_id     | int     | No       | Brand ID (optional)                         | 2       |
| description  | string  | No       | Description (optional)                      | "..."  |

---

## Request Example
```json
{
  "equipment_id": 10,
  "count": 5,
  "brand_id": 2,
  "description": "Brand new treadmill"
}
```

---

## Response

### 201 Created
Returns the created gym equipment resource.

#### Example
```json
{ /* gym equipment resource */ }
```

For a full schema, see [Gym Equipment Resource](gym_equipment_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 422    | Validation error           | [Validation error](../../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
