# PUT /api/v1/tracker/measurements/{tracker-measurement-id}

Update a body-measurement record.


---

## Permissions
| Permission                     | Description                |
|--------------------------------|----------------------------|
| `tracker_measurements.update`  | Update tracker measurement |

Only the athlete who logged the record may update it. A record belonging to somebody else — including
one visible through a tracker share — returns 403; share viewers are strictly read-only.

---

## Request Body Parameters
| Name         | Type    | Required | Description                                     |
|--------------|---------|----------|-------------------------------------------------|
| `tracked_at` | string  | No       | Datetime the measurements were taken            |
| `neck`       | float   | No       | Neck circumference in centimetres (1–300)       |
| `shoulder`   | float   | No       | Shoulder circumference in centimetres (1–300)   |
| `chest`      | float   | No       | Chest circumference in centimetres (1–300)      |
| `waist`      | float   | No       | Waist circumference in centimetres (1–300)      |
| `hip`        | float   | No       | Hip circumference in centimetres (1–300)        |
| `arm`        | float   | No       | Arm circumference in centimetres (1–300)        |
| `forearm`    | float   | No       | Forearm circumference in centimetres (1–300)    |
| `thigh`      | float   | No       | Thigh circumference in centimetres (1–300)      |
| `calf`       | float   | No       | Calf circumference in centimetres (1–300)       |
| `notes`      | string  | No       | Optional notes (max 2000 characters)            |

*All parameters are optional. If omitted, they will not be updated. Any of them may be set to `null`.*

Unlike `POST`, update does **not** require at least one measurement to remain: clearing the last
remaining site is the caller deliberately emptying the row, and refusing it would make a
measurement un-clearable.

---

## Response

### 200 OK
```json
{
  "data": { /* tracker measurement resource */ }
}
```
- See [Tracker Measurement Resource](tracker_measurement_resource.md)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 422    | Validation Error   | [Validation error](../../_globals/validation-errors.md)         |
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not Found          | [Not found error](../../_globals/not-found-errors.md)           |

---
