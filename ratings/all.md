# GET /api/v1/ratings/all

Retrieves all ratings in the system (admin only), with support for filtering and pagination.


---

## Permissions
| Permission         | Description                                 |
|--------------------|---------------------------------------------|
| `ratings.view_all` | View all ratings in the system (admin only) |

---

## Query Parameters
| Name      | Type   | Required | Description                                                                 | Example                |
|-----------|--------|----------|-----------------------------------------------------------------------------|------------------------|
| type      | string | No       | Ratable type (`App\Models\Gym`, `App\Models\TrainingService`). Comma-separated for multiple types | "App\\Models\\Gym,App\\Models\\TrainingService" |
| item_id   | int    | No       | Ratable ID(s) to filter by (comma-separated for multiple)                    | "1,2,3"               |
| user_id   | int    | No       | User ID(s) who rated (comma-separated for multiple)                          | "5,6"                 |
| from_date | string | No       | Start of date range (YYYY-MM-DD)                                            | "2024-01-01"          |
| to_date   | string | No       | End of date range (YYYY-MM-DD)                                              | "2024-01-31"          |
| from_score| int    | No       | Minimum score                                                               | 3                      |
| to_score  | int    | No       | Maximum score                                                               | 5                      |
| order     | string | No       | Order of results: `ASC` or `DESC` (default: `DESC`)                         | "DESC"                 |

---

## Response

### 200 OK
Returns a paginated list of rating resources.

#### Schema
```json
{
  "data": [
    { /* Rating Resource */ }
  ],
  "links": { /* Pagination Data */ },
  "meta": { /* Pagination Data */ }
}
```

#### Example
```json
{
  "data": [
    {
      "id": 123,
      "user_id": 42,
      "ratable_type": "App\\Models\\Gym",
      "ratable_id": 10,
      "score": 5
    }
  ],
  "links": {
    "first": "https://api.example.com/api/v1/ratings/all?page=1",
    "last": "https://api.example.com/api/v1/ratings/all?page=10",
    "prev": null,
    "next": "https://api.example.com/api/v1/ratings/all?page=2"
  },
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 10,
    "path": "https://api.example.com/api/v1/ratings/all",
    "per_page": 50,
    "to": 50,
    "total": 500
  }
}
```

For a full schema, see [Rating Resource](rating_resource.md) and [Pagination Data](../_globals/pagination-data.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../_globals/not-found-errors.md) |
