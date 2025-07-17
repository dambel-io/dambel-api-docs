# POST /api/v1/tracker/weights

Record a new weight in the tracker system.


---

## Permissions
| Permission                 | Description                |
|----------------------------|----------------------------|
| `tracker_weights.create`   | Create tracker weight      |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                 |
|--------------|---------|----------|---------------------------------------------|
| `tracked_at` | string  | Yes      | Datetime for the weight record              |
| `weight`     | float   | Yes      | Weight in kilograms (kg)                    |
| `notes`      | string  | No       | Optional notes                              |

---

## Response

### 201 Created
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
