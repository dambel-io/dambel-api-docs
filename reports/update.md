# `PUT /api/v1/reports/{report-id}`
You can update reports using this API.


## Permissions

- `reports.update`: To update your own report
- `reports.update_any`: To update any report

## Params

- `description`: Required content of the report (max length 255)
- `signed_off`: A boolean to draft the report (Only admin can change it)

All parameters are optional.

## Response

### 200 OK
```json
{
    "report": {<report resource>},
}
```

[Report Resource](report_resource.md)

### 422 Unprocessable Entity
[Validation error](../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)
