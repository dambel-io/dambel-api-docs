# PUT /api/v1/reports/{report-id}

Updates an existing report by its ID.


---

## Permissions
| Permission           | Description                        |
|----------------------|------------------------------------|
| `reports.update`     | Update your own report             |
| `reports.update_any` | Update any report                  |

---

## URL Parameters
| Name        | Type | Required | Description                | Example |
|-------------|------|----------|----------------------------|---------|
| report-id   | int  | Yes      | ID of the report to update | 123     |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                 | Example           |
|--------------|---------|----------|---------------------------------------------|-------------------|
| description  | string  | No       | Content of the report (max 255 chars)       | "Updated details" |
| signed_off   | bool    | No       | Whether the report is signed off (admin only) | true              |

All parameters are optional; only include fields you wish to update.

---

## Request Example
```json
{
  "description": "Updated details about the issue.",
  "signed_off": true
}
```

---

## Response

### 200 OK
Returns the updated report resource.

#### Example
```json
{
  "report": {
    "id": 123,
    "reportable_type": "App\\Models\\Gym",
    "reportable_id": 456,
    "user_id": 789,
    "description": "Updated details about the issue.",
    "signed_off": true,
    "created_at": "2020-01-01 00:00:00"
  }
}
```

For a full schema, see [Report Resource](report_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 422    | Validation error           | [Validation error](../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
