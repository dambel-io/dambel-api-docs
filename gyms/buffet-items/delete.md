# DELETE /api/v1/gyms/{gym-id}/buffet-items/{buffet-item-id}

Deletes a buffet item from a gym by its ID.


---

## Permissions
| Permission                    | Description                                         |
|-------------------------------|-----------------------------------------------------|
| `gym_buffet_items.delete`     | Delete buffet items from your own gym               |
| `gym_buffet_items.delete_any` | Delete buffet items from any gym (admin only)       |

---

## Path Parameters
| Name           | Type | Required | Description                | Example |
|----------------|------|----------|----------------------------|---------|
| gym-id         | int  | Yes      | ID of the gym              | 123     |
| buffet-item-id | int  | Yes      | ID of the buffet item      | 5       |

---

## Response

### 204 No Content
Buffet item was successfully deleted. No response body is returned.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../../_globals/not-found-errors.md) |
