# `DELETE /api/v1/admin/brands/{brand-id}`

Delete a brand. Optionally transfer attached data to another brand.


---

## Permissions
| Permission         | Description         |
|--------------------|---------------------|
| `brands.view_all`  | Access brands       |
| `brands.delete`    | Delete any brand    |

---

## Request Body Parameters
| Name             | Type    | Required | Description                                                      |
|------------------|---------|----------|------------------------------------------------------------------|
| `replacement_id` | integer | No       | ID of another brand to transfer attached data (optional)         |

---

## Response

### 204 No Content
No content is returned when the brand is deleted successfully.

---

## Error Responses
- **400 Bad Request:** When brand has data and `replacement_id` is not provided or is not valid. Number of attached items is returned in `attached_data`.
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)
- **404 Not Found:** [Not-found error](../../_globals/not-found-errors.md)

---
