# `DELETE /api/v1/reports/{report-id}`
You can delete a report using this API.


## Permissions

- You need to have **view** permission of the **reportable**
- `reports.delete`: To delete your own reports
- `reports.delete_any`: To delete any report

## Response

### 204 No Content
No content when report gets deleted

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../_globals/not-found-errors.md)
