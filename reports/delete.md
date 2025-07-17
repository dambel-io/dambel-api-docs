# DELETE /api/v1/reports/{report-id}

Deletes a specific report by its ID.


---

## Permissions
| Permission         | Description                        |
|--------------------|------------------------------------|
| `reports.delete`   | Delete your own reports            |
| `reports.delete_any` | Delete any report                |

---

## URL Parameters
| Name        | Type | Required | Description                | Example |
|-------------|------|----------|----------------------------|---------|
| report-id   | int  | Yes      | ID of the report to delete | 123     |

---

## Request Example
```
DELETE /api/v1/reports/123
Authorization: Bearer {token}
```

---

## Response

### 204 No Content
No content is returned when the report is successfully deleted.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 404    | Report not found           | [Not-found error](../_globals/not-found-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |

---

## Resource Schema
This endpoint does not return a resource body on success.
