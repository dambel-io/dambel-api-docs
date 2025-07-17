# `DELETE /api/v1/admin/majors/{major-id}`

Delete a major. Optionally transfer attached data to another major.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `majors.view_all`     | Access majors       |
| `majors.delete`       | Delete major        |

---

## Request Body Parameters
| Name             | Type    | Required | Description                                                      |
|------------------|---------|----------|------------------------------------------------------------------|
| `replacement_id` | integer | No       | ID of another major to transfer attached data (optional)          |

---

## Response

### 204 No Content
No content is returned when the major is deleted successfully.

---

## Error Responses
- **400 Bad Request:** When major has data and `replacement_id` is not provided or is not valid. Number of attached items is returned in `attached_data`.
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)
- **404 Not Found:** [Not-found error](../../_globals/not-found-errors.md)

---
