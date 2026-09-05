# Tracker Measurement Resource

Represents one set of body measurements in the tracker system.


---

## Schema
| Field         | Type          | Description                                              |
|---------------|---------------|----------------------------------------------------------|
| `id`          | integer       | Measurement record ID                                    |
| `user_id`     | integer       | User ID                                                  |
| `tracked_at`  | string        | Datetime of the record (YYYY-MM-DD HH:MM:SS)             |
| `neck`        | float \| null | Neck circumference in centimetres                        |
| `shoulder`    | float \| null | Shoulder circumference in centimetres                    |
| `chest`       | float \| null | Chest circumference in centimetres                       |
| `waist`       | float \| null | Waist circumference in centimetres                       |
| `hip`         | float \| null | Hip circumference in centimetres                         |
| `arm`         | float \| null | Arm circumference in centimetres                         |
| `forearm`     | float \| null | Forearm circumference in centimetres                     |
| `thigh`       | float \| null | Thigh circumference in centimetres                       |
| `calf`        | float \| null | Calf circumference in centimetres                        |
| `notes`       | string \| null| Notes                                                    |

Every site is always present. A site that was not measured is `null` rather than omitted, so a
client never has to tell "not sent" from "not measured".

---

## Example
```json
{
  "id": 123,
  "user_id": 7,
  "tracked_at": "2026-09-04 08:00:00",
  "neck": null,
  "shoulder": null,
  "chest": 102.5,
  "waist": 84.5,
  "hip": null,
  "arm": null,
  "forearm": null,
  "thigh": null,
  "calf": null,
  "notes": "morning, fasted"
}
```

---
