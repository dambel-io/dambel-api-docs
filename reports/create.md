# POST /api/v1/reports

Creates a new report for a specified element (e.g., gym, user).


---

## Permissions
| Permission         | Description                        |
|--------------------|------------------------------------|
| `reports.create`   | Create a report                    |

---

## Request Body Parameters
| Name            | Type    | Required | Description                                 | Example         |
|-----------------|---------|----------|---------------------------------------------|-----------------|
| reportable_type | string  | Yes      | Type of the element to report (e.g., `gym`) | "gym"          |
| reportable_id   | int     | Yes      | ID of the element to report                 | 456             |
| description     | string  | Yes      | Description of the report (max 255 chars)   | "Broken equipment" |

---

## Request Example
```json
{
  "reportable_type": "gym",
  "reportable_id": 456,
  "description": "Broken equipment"
}
```

---

## Response

### 201 Created
Returns the created report resource.

#### Example
```json
{
  "report": {
    "id": 123,
    "reportable_type": "App\\Models\\Gym",
    "reportable_id": 456,
    "user_id": 789,
    "description": "Broken equipment",
    "signed_off": false,
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
