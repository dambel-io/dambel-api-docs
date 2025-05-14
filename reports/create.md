# `POST /api/v1/reports`
You can create report using this API.


## Permissions

- `reports.create`: To create report

## Params

- `reportable_type`: Type of the element that you are adding report to
- `reportable_id`: Id of the element
- `description`: Required content of the report (max length 255)

## Response

### 201 Created
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
