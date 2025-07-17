# PUT /api/v1/tracker/waters/{tracker-water-id}

Update a water intake record in the tracker system.


---

## Permissions
| Permission                | Description                |
|---------------------------|----------------------------|
| `tracker_waters.update`   | Update tracker water record|

---

## Request Body Parameters
| Name         | Type    | Required | Description                                 |
|--------------|---------|----------|---------------------------------------------|
| `tracked_at` | string  | No       | Datetime for the water intake               |
| `glass_count`| float   | No       | Number of glasses (float)                   |
| `notes`      | string  | No       | Optional notes                              |

*All parameters are optional. If omitted, they will not be updated. You can set them to null if desired.*

---

## Response

### 200 OK
```
<tracker water resource>
```
- See [Tracker Water Resource](tracker_water_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 422    | Validation Error   | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
