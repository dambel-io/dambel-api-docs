# `/api/v1/training/services`

Retrieve a list of training services for a user.


**No authentication required.**

---

## Query Parameters
| Name       | Type    | Required | Description                                                      |
|------------|---------|----------|------------------------------------------------------------------|
| `user_id`  | string  | No       | Filter by user IDs (comma-separated for multiple)                |
| `category` | string  | No       | Filter by categories (comma-separated): `diet_plan`, `workout_plan`, `other` |
| `major_ids`| string  | No       | Filter by major IDs (comma-separated for multiple)               |
| `search`   | string  | No       | Search by title, description, and trainer name                                  |
| `page`     | int     | No       | Page number for pagination                                       |
| `sort`     | string  | No       | `asc` for oldest, `desc` for latest (default: `desc`)            |

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
