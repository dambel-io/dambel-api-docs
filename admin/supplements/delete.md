# `DELETE /api/v1/admin/supplements/{supplement-id}`

Delete a supplement. Optionally transfer attached data to another supplement.


---

## Permissions
| Permission               | Description         |
|--------------------------|---------------------|
| `supplements.view_all`   | Access supplements  |
| `supplements.delete`     | Delete supplement   |

---

## Request Body Parameters
| Name             | Type    | Required | Description                                                      |
|------------------|---------|----------|------------------------------------------------------------------|
| `replacement_id` | integer | No       | ID of another supplement to transfer attached data (optional)     |

---

## Response

### 204 No Content
No content is returned when the supplement is deleted successfully.

---

## Error Responses
- **400 Bad Request:** When supplement has data and `replacement_id` is not provided or is not valid. Number of attached items is returned in `attached_data`.
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)
- **404 Not Found:** [Not-found error](../../_globals/not-found-errors.md)

---
