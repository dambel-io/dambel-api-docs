# POST /api/v1/tracker/sleeps

Record a new sleep in the tracker system.


---

## Permissions
| Permission                | Description                |
|---------------------------|----------------------------|
| `tracker_sleeps.create`   | Create tracker sleep       |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                 |
|--------------|---------|----------|---------------------------------------------|
| `tracked_at` | string  | Yes      | Datetime for the sleep record               |
| `notes`      | string  | No       | Optional notes                              |

---

## Response

### 201 Created
```
<tracker sleep resource>
```
- See [Tracker Sleep Resource](tracker_sleep_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 422    | Validation Error   | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
