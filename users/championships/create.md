# POST /api/v1/users/{user-id}/championships

Create a championship record for a user.


---

## Permissions
| Permission                  | Description                                 |
|-----------------------------|---------------------------------------------|
| `championships.create`      | Create championships for yourself           |
| `championships.create_any`  | Create championships for any user           |

---

## Request Body Parameters
| Name          | Type    | Required | Description                        |
|---------------|---------|----------|------------------------------------|
| `title`       | string  | Yes      | Title of the championship (max 255)|
| `description` | string  | No       | Optional description (max 2000)    |
| `date`        | string  | Yes      | Date of the championship (date)    |

---

## Response

### 201 Created
```json
{ /* championship resource */ }
```
- [Championship Resource](championship_resource.md)

---

## Error Responses
| Status | Description               | Reference                                                       |
|--------|---------------------------|-----------------------------------------------------------------|
| 422    | Validation error          | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized              | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission) | [Permission error](../../_globals/permission-errors.md)         |

---
