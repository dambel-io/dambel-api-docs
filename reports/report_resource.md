# Report Resource

Represents a report entity, including its associations, description, status, and timestamps.


---

## Schema
| Field           | Type    | Description                                      | Example                |
|-----------------|---------|--------------------------------------------------|------------------------|
| id              | int     | Unique identifier for the report                 | 123                    |
| reportable_type | string  | Type of the reportable (e.g., `App\\Models\\Gym`) | "App\\Models\\Gym"      |
| reportable_id   | int     | ID of the reportable item                        | 456                    |
| user_id         | int     | ID of the user who created the report            | 789                    |
| description     | string  | Description of the report                        | "Broken equipment"     |
| signed_off      | bool    | Whether the report has been signed off           | false                  |
| created_at      | string  | Creation timestamp (ISO 8601 format)             | "2020-01-01 00:00:00" |

---

## Example
```json
{
  "id": 123,
  "reportable_type": "App\\Models\\Gym",
  "reportable_id": 456,
  "user_id": 789,
  "description": "Broken equipment reported.",
  "signed_off": false,
  "created_at": "2020-01-01 00:00:00"
}
```
