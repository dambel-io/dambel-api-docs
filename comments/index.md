# GET /api/v1/comments

Retrieves a list of comments, with support for filtering by resource type, item, user, and content. Useful for both admin management and fetching comments for a specific profile.


---

## Permissions
| Permission         | Description                                                                 |
|--------------------|-----------------------------------------------------------------------------|
| `comments.view`    | View your own comments and comments on any public commentable                |
| `comments.view_all`| View all comments, including drafts, on any profile (admin only)             |

---

## Query Parameters

| Name     | Type   | Required | Description                                                                 | Example                |
|----------|--------|----------|-----------------------------------------------------------------------------|------------------------|
| type     | string | No       | The commentable type (`App\Models\Gym`, `App\Models\Post`). Comma-separated for multiple types | "App\\Models\\Gym,App\\Models\\Post" |
| item_id  | int    | No       | ID of the commentable. Comma-separated for multiple IDs                      | "1,2,3"               |
| user_id  | int    | No       | ID of the user. Comma-separated for multiple IDs                             | "5,6"                 |
| search   | string | No       | Search term for comment content                                             | "great"               |
| order    | string | No       | Order of results: `ASC` or `DESC` (default: `DESC`)                         | "DESC"                 |

---

## Response

### 200 OK
Returns a paginated list of comment resources.

#### Schema
```json
{
  "data": [
    { /* Comment Resource */ }
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
      "user_id": 456,
      "commentable_type": "App\\Models\\Gyms\\Gym",
      "commentable_id": 42,
      "content": "Great gym!",
      "parent_comment_id": null,
      "created_at": "2025-01-01 00:00:00",
      "updated_at": "2025-01-01 00:03:00"
    }
  ],
  "links": {
    "first": "https://api.example.com/api/v1/comments?page=1",
    "last": "https://api.example.com/api/v1/comments?page=10",
    "prev": null,
    "next": "https://api.example.com/api/v1/comments?page=2"
  },
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 10,
    "path": "https://api.example.com/api/v1/comments",
    "per_page": 50,
    "to": 50,
    "total": 500
  }
}
```

For a full schema, see [Comment Resource](comment_resource.md) and [Pagination Data](../_globals/pagination-data.md).

---

### Error Responses

| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../_globals/not-found-errors.md) |
