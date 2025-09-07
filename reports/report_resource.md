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
| ai_marked_spam  | bool    | Whether the report has been marked as spam by AI | false                  |
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
  "ai_marked_spam": false,
  "created_at": "2020-01-01 00:00:00"
}
```

### AI Marked Spam
The AI system will automatically check each newly created report and marks the spam ones.
So admins can exclude them while checking the reports for a better performance.
