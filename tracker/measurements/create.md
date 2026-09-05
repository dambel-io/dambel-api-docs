# POST /api/v1/tracker/measurements

Record a new set of body measurements.


---

## Permissions
| Permission                     | Description                |
|--------------------------------|----------------------------|
| `tracker_measurements.create`  | Create tracker measurement |

---

## Request Body Parameters
| Name         | Type    | Required | Description                                     |
|--------------|---------|----------|-------------------------------------------------|
| `tracked_at` | string  | Yes      | Datetime the measurements were taken            |
| `neck`       | float   | See below | Neck circumference in centimetres (1–300)      |
| `shoulder`   | float   | See below | Shoulder circumference in centimetres (1–300)  |
| `chest`      | float   | See below | Chest circumference in centimetres (1–300)     |
| `waist`      | float   | See below | Waist circumference in centimetres (1–300)     |
| `hip`        | float   | See below | Hip circumference in centimetres (1–300)       |
| `arm`        | float   | See below | Arm circumference in centimetres (1–300)       |
| `forearm`    | float   | See below | Forearm circumference in centimetres (1–300)   |
| `thigh`      | float   | See below | Thigh circumference in centimetres (1–300)     |
| `calf`       | float   | See below | Calf circumference in centimetres (1–300)      |
| `notes`      | string  | No       | Optional notes (max 2000 characters)            |

**At least one measurement is required.** Each of the nine sites carries
`required_without_all` naming the other eight, so a request with a `tracked_at` and no measurement
at all is a 422 listing all nine fields rather than an empty record. Every site is optional once
any one of them is present.

`user_id` is taken from the authenticated token and is never read from the request body.

All measurements are in **centimetres**. Nothing derived (BMI, ratios) is stored — `users.height`
is available for a client that wants to compute one.

---

## Response

### 201 Created
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

---
