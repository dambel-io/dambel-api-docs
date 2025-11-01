# POST /api/v1/tracker/supplements

Record a new supplement in the tracker system.


---

## Permissions
| Permission                      | Description                      |
|----------------------------------|----------------------------------|
| `tracker_supplements.create`     | Create tracker supplement record |

---

## Request Body Parameters
| Name             | Type    | Required | Description                                 |
|------------------|---------|----------|---------------------------------------------|
| `tracked_at`     | string  | Yes      | Datetime for the supplement record          |
| `supplement_id`  | int     | Yes      | Supplement ID                              |
| `diet_plan_supplement_id` | int | No | Diet Plan Supplement ID |
| `notes`          | string  | No       | Optional notes                              |

---

## Response

### 201 Created
```
<tracker supplement resource>
```
- See [Tracker Supplement Resource](tracker_supplement_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 422    | Validation Error   | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
