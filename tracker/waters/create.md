# POST /api/v1/tracker/waters

Record a new water intake in the tracker system.


---

## Permissions
| Permission                | Description                |
|---------------------------|----------------------------|
| `tracker_waters.create`   | Create tracker water record|

---

## Request Body Parameters
| Name         | Type    | Required | Description                                 |
|--------------|---------|----------|---------------------------------------------|
| `tracked_at` | string  | Yes      | Datetime for the water intake               |
| `glass_count`| float   | Yes      | Number of glasses (float)                   |
| `notes`      | string  | No       | Optional notes                              |

---

## Response

### 201 Created
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
