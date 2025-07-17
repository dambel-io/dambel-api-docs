# DELETE /api/v1/gyms/{gym-id}/admins/{admin-id}

Deletes an admin from a gym by their ID.


---

## Permissions
| Permission             | Description                                         |
|------------------------|-----------------------------------------------------|
| `gym_admins.delete`    | Delete admins from your own gyms                    |
| `gym_admins.delete_any`| Delete admins from any gym (admin only)             |

---

## Path Parameters
| Name      | Type | Required | Description           | Example |
|-----------|------|----------|-----------------------|---------|
| gym-id    | int  | Yes      | ID of the gym         | 123     |
| admin-id  | int  | Yes      | ID of the admin to delete | 5   |

---

## Response

### 204 No Content
Admin was successfully deleted. No response body is returned.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../../_globals/not-found-errors.md) |
