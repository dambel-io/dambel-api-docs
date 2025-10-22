# `/api/v1/training/services/{training-service-id}`

Update a training service.


---

## Permissions
| Permission                 | Description                                         |
|----------------------------|-----------------------------------------------------|
| `training_services.update` | Update your own training services                   |
| `training_services.update_any` | Update training services for any user            |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                 |
|--------------|---------|----------|---------------------------------------------|
| `title`      | string  | No       | Title of the training service (max 255)     |
| `description`| string  | No       | Description (max 2000, optional)            |
| `price`      | int     | No       | Price of the training service               |
| `discount`   | float   | No       | Discount percentage (nullable, default 0)   |
| `category`   | string  | No       | Category of training service: `diet_plan`, `workout_plan`, `other` |
| `major_ids`  | array   | No       | Array of major IDs that this training service covers |

*All parameters are optional. If omitted, they will not be updated. You can set them to null if desired.*

---

## Response

### 200 OK
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
