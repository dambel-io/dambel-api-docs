# `POST /api/v1/users/{user-id}/education`

Create an education record for a user.


---

## Permissions
| Permission             | Description                                 |
|------------------------|---------------------------------------------|
| `education.create`     | Create education for yourself               |
| `education.create_any` | Create education for any user               |

---

## Request Body Parameters
| Name          | Type    | Required | Description                        |
|---------------|---------|----------|------------------------------------|
| `school`      | string  | Yes      | Name of the school (max 255)       |
| `field`       | string  | Yes      | Field of education (max 255)       |
| `description` | string  | No       | Optional description (max 2000)    |
| `start_date`  | string  | Yes      | Start date (date format)           |
| `end_date`    | string  | No       | End date (nullable, date format)   |

---

## Response

### 201 Created
```
<education resource>
```
- [Education Resource](education_resource.md)

---

## Error Responses
- **422 Unprocessable Entity:** [Validation error](../../_globals/validation-errors.md)
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)

---
