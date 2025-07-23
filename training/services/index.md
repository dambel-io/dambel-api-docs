# `/api/v1/training/services`

Retrieve a list of training services for a user.


---

## Query Parameters
| Name      | Type    | Required | Description                                                      |
|-----------|---------|----------|------------------------------------------------------------------|
| `user_id` | string  | No       | Filter by user IDs (comma-separated for multiple)                |
| `search`  | string  | No       | Search by title and description                                  |
| `page`    | int     | No       | Page number for pagination                                       |
| `sort`    | string  | No       | `asc` for oldest, `desc` for latest (default: `desc`)            |

> **Note:** Results are first sorted by marketing boosts; `sort` applies secondarily.

---

## Response

### 200 OK
```json
{
  "data": [<training service resource>, ...],
  "links": {<pagination data>},
  "meta": {<pagination data>}
}
```
- See [Training Service Resource](training_service_resource.md)
- See [Pagination Data](../../_globals/pagination-data.md) (per page: 50)

---

## Error Responses
| Status | Error Type         | Reference                                                      |
|--------|--------------------|----------------------------------------------------------------|
| 401    | Unauthorized       | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden          | [Permission error](../../_globals/permission-errors.md)         |
| 404    | Not Found          | [Not-found error](../../_globals/not-found-errors.md)           |

---
