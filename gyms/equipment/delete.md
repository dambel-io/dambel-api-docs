# DELETE /api/v1/gyms/{gym-id}/equipment/{gym-equipment-id}

Deletes a specific equipment entry from a gym.


---

## Permissions
| Permission                | Description                                 |
|---------------------------|---------------------------------------------|
| `gym_equipment.delete`    | Delete equipment from your own gyms         |
| `gym_equipment.delete_any`| Delete equipment from any gym               |

---

## URL Parameters
| Name              | Type | Required | Description                | Example |
|-------------------|------|----------|----------------------------|---------|
| gym-id            | int  | Yes      | ID of the gym              | 123     |
| gym-equipment-id  | int  | Yes      | ID of the gym equipment    | 55      |

---

## Request Example
```
DELETE /api/v1/gyms/123/equipment/55
Authorization: Bearer {token}
```

---

## Response

### 204 No Content
No content is returned when the equipment is successfully deleted.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../../_globals/not-found-errors.md) |
