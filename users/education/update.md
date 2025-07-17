# `PUT /api/v1/users/{user-id}/education/{education-id}`

Update an education record for a user.


---

## Permissions
| Permission             | Description                                 |
|------------------------|---------------------------------------------|
| `education.update`     | Update your own education                   |
| `education.update_any` | Update education for any user               |

---

## Request Body Parameters
| Name          | Type    | Required | Description                        |
|---------------|---------|----------|------------------------------------|
| `school`      | string  | No       | Name of the school (max 255)       |
| `field`       | string  | No       | Field of education (max 255)       |
| `description` | string  | No       | Optional description (max 2000)    |
| `start_date`  | string  | No       | Start date (date format)           |
| `end_date`    | string  | No       | End date (nullable, date format)   |

*All parameters are optional. If omitted, they will not be updated.*

---

## Response

### 200 OK
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
