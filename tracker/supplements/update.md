# PUT /api/v1/tracker/supplements/{tracker-supplement-id}

Update a supplement record in the tracker system.


---

## Permissions
| Permission                      | Description                      |
|----------------------------------|----------------------------------|
| `tracker_supplements.update`     | Update tracker supplement record |

---

## Request Body Parameters
| Name             | Type    | Required | Description                                 |
|------------------|---------|----------|---------------------------------------------|
| `tracked_at`     | string  | No       | Datetime for the supplement record          |
| `supplement_id`  | int     | No       | Supplement ID                              |
| `diet_plan_supplement_id` | int | No | Diet Plan Supplement ID |
| `notes`          | string  | No       | Optional notes                              |

*All parameters are optional. If omitted, they will not be updated. You can set them to null if desired.*

---

## Response

### 200 OK
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
