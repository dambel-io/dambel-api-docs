# `/api/v1/training/services/{training-service-id}`

Delete a training service from a user.


---

## Permissions
| Permission                 | Description                                         |
|----------------------------|-----------------------------------------------------|
| `training_services.delete` | Delete your own training services                   |
| `training_services.delete_any` | Delete training services from any user           |

---

## Request Body Parameters
_None._

---

## Response

### 204 No Content
No content is returned when the training service is deleted successfully.

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not Found          | [Not-found error](../../_globals/not-found-errors.md)           |

---
