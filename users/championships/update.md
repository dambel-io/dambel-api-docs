# `PUT /api/v1/users/{user-id}/championships/{championship-id}`

Update a championship record for a user.


---

## Permissions
| Permission                  | Description                                 |
|-----------------------------|---------------------------------------------|
| `championships.update`      | Update your own championships               |
| `championships.update_any`  | Update championships for any user           |

---

## Request Body Parameters
| Name          | Type    | Required | Description                        |
|---------------|---------|----------|------------------------------------|
| `title`       | string  | No       | Title of the championship (max 255)|
| `description` | string  | No       | Optional description (max 2000)    |
| `date`        | string  | No       | Date of the championship (date)    |

*All parameters are optional. If omitted, they will not be updated.*

---

## Response

### 200 OK
```
<championship resource>
```
- [Championship Resource](championship_resource.md)

---

## Error Responses
- **422 Unprocessable Entity:** [Validation error](../../_globals/validation-errors.md)
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)

---
