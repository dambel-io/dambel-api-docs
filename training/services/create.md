# `/api/v1/training/services/{user-id}`

Create a new training service for a user.


---

## Permissions
| Permission                 | Description                                         |
|----------------------------|-----------------------------------------------------|
| `training_services.create` | Create training services for yourself               |
| `training_services.create_any` | Create training services for any user            |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                 |
|--------------|---------|----------|---------------------------------------------|
| `title`      | string  | Yes      | Title of the training service (max 255)     |
| `description`| string  | No       | Description (max 2000, optional)            |
| `price`      | int     | Yes      | Price of the training service               |
| `discount`   | float   | No       | Discount percentage (nullable, default 0)   |

*The user ID is specified in the route parameter.*

---

## Response

### 201 Created
```
<training service resource>
```
- See [Training Service Resource](training_service_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 422    | Validation Error   | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
