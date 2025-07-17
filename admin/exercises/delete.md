# `DELETE /api/v1/admin/exercises/{exercise-id}`

Delete an exercise. Optionally transfer attached data to another exercise.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `exercises.view_all`  | Access exercises    |
| `exercises.delete`    | Delete exercise     |

---

## Request Body Parameters
| Name             | Type    | Required | Description                                                      |
|------------------|---------|----------|------------------------------------------------------------------|
| `replacement_id` | integer | No       | ID of another exercise to transfer attached data (optional)       |

---

## Response

### 204 No Content
No content is returned when the exercise is deleted successfully.

---

## Error Responses
- **400 Bad Request:** When exercise has data and `replacement_id` is not provided or is not valid. Number of attached items is returned in `attached_data`.
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)
- **404 Not Found:** [Not-found error](../../_globals/not-found-errors.md)

---
