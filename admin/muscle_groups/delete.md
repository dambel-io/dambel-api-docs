# DELETE /api/v1/admin/muscle-groups/{muscle-group-id}

Delete a muscle group. Optionally transfer attached data to another muscle group.


---

## Permissions
| Permission               | Description          |
|--------------------------|----------------------|
| `muscle_groups.view_all` | Access muscle groups |
| `muscle_groups.delete`   | Delete muscle group  |

---

## Request Body Parameters
| Name             | Type    | Required | Description                                                             |
|------------------|---------|----------|-------------------------------------------------------------------------|
| `replacement_id` | integer | No       | ID of another muscle group to transfer attached data (optional)          |

---

## Response

### 204 No Content
No content is returned when the muscle group is deleted successfully.

---

## Error Responses
| Status | Description                                                                                                                                | Reference                                                       |
|--------|--------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------|
| 400    | When muscle group has data and `replacement_id` is not provided or is not valid. Number of attached items is returned in `attached_data`. |                                                                 |
| 401    | Unauthorized                                                                                                                               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)                                                                                                                  | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not found                                                                                                                                  | [Not-found error](../../_globals/not-found-errors.md)           |

---
