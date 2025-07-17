# `/api/v1/training/diet-plans`

Retrieve a list of your own and your trainees' diet plans.


---

## Permissions
| Permission        | Description                |
|-------------------|----------------------------|
| `diet_plans.view` | View diet plans            |

---

## Query Parameters
| Name         | Type    | Required | Description                                                      |
|--------------|---------|----------|------------------------------------------------------------------|
| `trainee_id` | string  | No       | Filter by trainee IDs (comma-separated for multiple)             |
| `search`     | string  | No       | Search by title and description                                  |
| `page`       | int     | No       | Page number for pagination                                       |
| `sort`       | string  | No       | `asc` for oldest, `desc` for latest (default: `desc`)            |

---

## Response

### 200 OK
```
{
  "data": [<diet plan resource>, ...],
  "links": {<pagination data>},
  "meta": {<pagination data>}
}
```
- See [Diet Plan Resource](diet_plan_resource.md)
- See [Pagination Data](../../_globals/pagination-data.md) (per page: 50)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |

---
