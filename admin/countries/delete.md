# `DELETE /api/v1/admin/countries/{country-id}`

Delete a country. Optionally transfer attached data to another country.


---

## Permissions
| Permission            | Description         |
|-----------------------|---------------------|
| `countries.view_all`  | Access countries    |
| `countries.delete`    | Delete any country  |

---

## Request Body Parameters
| Name             | Type    | Required | Description                                                      |
|------------------|---------|----------|------------------------------------------------------------------|
| `replacement_id` | integer | No       | ID of another country to transfer attached data (optional)       |

---

## Response

### 204 No Content
No content is returned when the country is deleted successfully.

---

## Error Responses
- **400 Bad Request:** When country has data and `replacement_id` is not provided or is not valid. Number of attached items is returned in `attached_data`.
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)
- **404 Not Found:** [Not-found error](../../_globals/not-found-errors.md)

---
