# PUT /api/v1/gyms/{gym-id}/equipment/{equipment-id}

Updates a specific gym equipment entry.


---

## Permissions
| Permission                | Description                                 |
|---------------------------|---------------------------------------------|
| `gym_equipment.update`    | Update equipment for your own gyms          |
| `gym_equipment.update_any`| Update equipment for any gym                |

---

## URL Parameters
| Name         | Type | Required | Description                | Example |
|--------------|------|----------|----------------------------|---------|
| gym-id       | int  | Yes      | ID of the gym              | 123     |
| equipment-id | int  | Yes      | ID of the gym equipment    | 55      |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                 | Example |
|--------------|---------|----------|---------------------------------------------|---------|
| count        | int     | No       | Number of this equipment in the gym         | 10      |
| brand_id     | int     | No       | Brand ID (optional)                         | 2       |
| description  | string  | No       | Description (optional)                      | "..."  |

All parameters are optional; only include fields you wish to update. You can set them to null to clear their value.

---

## Request Example
```json
{
  "count": 10,
  "brand_id": 2,
  "description": "Updated description"
}
```

---

## Response

### 200 OK
Returns the updated gym equipment resource.

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
