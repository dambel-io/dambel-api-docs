# GET /api/v1/ratings

Retrieves a list of ratings created by the authenticated user. Supports filtering and pagination.


---

## Query Parameters
See [`/all`](all.md#params) for available query parameters.

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
    "first": "https://api.example.com/api/v1/ratings?page=1",
    "last": "https://api.example.com/api/v1/ratings?page=10",
    "prev": null,
    "next": "https://api.example.com/api/v1/ratings?page=2"
  },
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 10,
    "path": "https://api.example.com/api/v1/ratings",
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
