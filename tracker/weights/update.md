# PUT /api/v1/tracker/weights/{tracker-weight-id}

Update a weight record in the tracker system.


---

## Permissions
| Permission                 | Description                |
|----------------------------|----------------------------|
| `tracker_weights.update`   | Update tracker weight      |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                 |
|--------------|---------|----------|---------------------------------------------|
| `tracked_at` | string  | No       | Datetime for the weight record              |
| `weight`     | float   | No       | Weight in kilograms (kg)                    |
| `notes`      | string  | No       | Optional notes                              |

*All parameters are optional. If omitted, they will not be updated. You can set them to null if desired.*

---

## Response

### 200 OK
```
<tracker weight resource>
```
- See [Tracker Weight Resource](tracker_weight_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 422    | Validation Error   | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
