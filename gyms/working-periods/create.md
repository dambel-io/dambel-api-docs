# POST /api/v1/gyms/{gym-id}/working-periods

Creates a new working period for a gym.


---

## Permissions
| Permission                    | Description                                 |
|-------------------------------|---------------------------------------------|
| `gym_working_periods.create`  | Create working periods for your own gyms    |
| `gym_working_periods.create_any` | Create working periods for any gym         |

---

## URL Parameters
| Name    | Type | Required | Description                | Example |
|---------|------|----------|----------------------------|---------|
| gym-id  | int  | Yes      | ID of the gym              | 123     |

---

## Request Body Parameters
| Name                | Type    | Required | Description                                 | Example         |
|---------------------|---------|----------|---------------------------------------------|-----------------|
| day                 | string  | Yes      | Day of the week (`saturday`-`friday`)       | "monday"       |
| gender              | string  | Yes      | `men`, `women`, or `genderless`             | "women"        |
| opens_at            | string  | Yes      | Opening time (HH:mm)                        | "07:00"        |
| closes_at           | string  | Yes      | Closing time (HH:mm)                        | "23:30"        |
| description         | string  | No       | Description (max 2000 chars, optional)      | "Some desc"    |
| is_exception        | bool    | No       | Whether this is for an exceptional date      | false           |
| exception_start_date| string  | No       | Start date of the exception (YYYY-MM-DD)    | null            |
| exception_end_date  | string  | No       | End date of the exception (YYYY-MM-DD)      | null            |

---

## Request Example
```json
{
  "day": "monday",
  "gender": "women",
  "opens_at": "07:00",
  "closes_at": "23:30",
  "description": "Some desc",
  "is_exception": false
}
```

---

## Response

### 201 Created
Returns the created working period resource.

#### Example
```json
{ /* working period resource */ }
```

For a full schema, see [Working Period Resource](gym_working_period_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 422    | Validation error           | [Validation error](../../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
