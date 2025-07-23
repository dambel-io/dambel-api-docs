# `GET /api/v1/training/workout-plans`

Retrieve a list of your own and your trainees' workout plans.


---

## Permissions
| Permission             | Description                |
|------------------------|----------------------------|
| `workout_plans.view`   | View workout plans         |

---

## Query Parameters
| Name         | Type    | Required | Description                                                      |
|--------------|---------|----------|------------------------------------------------------------------|
| `trainee_id` | string  | No       | Comma-separated trainee IDs to filter                            |
| `search`     | string  | No       | Search by title or description                                   |
| `page`       | int     | No       | Page number for pagination                                       |
| `sort`       | string  | No       | `asc` for oldest, `desc` for latest (default: `desc`)            |

---

## Response

### 200 OK
```json
{
  "data": [<workout plan resource>, ...],
  "links": {<pagination data>},
  "meta": {<pagination data>}
}
```
- [Workout Plan Resource](workout_plan_resource.md)
- [Pagination Data](../../_globals/pagination-data.md) (per page: 50)

---

## Error Responses
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)

---
