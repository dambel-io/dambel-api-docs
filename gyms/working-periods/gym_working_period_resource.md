# Gym Working Period Resource

Represents a working period for a gym, including day, gender, opening/closing times, and exception details.


---

## Schema
| Field                | Type    | Description                                 | Example         |
|----------------------|---------|---------------------------------------------|-----------------|
| id                   | int     | Unique identifier for the working period    | 123             |
| gym_id               | int     | ID of the gym                               | 123             |
| day                  | string  | Day of the week                             | "monday"        |
| gender               | string  | Gender restriction (`men`, `women`, `genderless`) | "women"   |
| opens_at             | string  | Opening time (HH:mm)                        | "07:00"         |
| closes_at            | string  | Closing time (HH:mm)                        | "23:30"         |
| description          | string  | Description (nullable)                      | "Some desc"     |
| is_exception         | bool    | Whether this is for an exceptional date     | false            |
| exception_start_date | string  | Start date of the exception (nullable)      | null             |
| exception_end_date   | string  | End date of the exception (nullable)        | null             |

---

## Example
```json
{
  "id": 123,
  "gym_id": 123,
  "day": "monday",
  "gender": "women",
  "opens_at": "07:00",
  "closes_at": "23:30",
  "description": "Some desc",
  "is_exception": false,
  "exception_start_date": null,
  "exception_end_date": null
}
```
