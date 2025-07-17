# GET /api/v1/posts

Retrieves a list of posts, with support for filtering by profile type, profile ID, search, and order. Useful for both admin management and fetching posts for a specific profile.


---

## Permissions
| Permission         | Description                                                                 |
|--------------------|-----------------------------------------------------------------------------|
| `posts.view`       | View your own posts and posts on any public profile                         |
| `posts.view_all`   | View all posts, including drafts, on any profile (admin only)                |

---

## Query Parameters
| Name      | Type   | Required | Description                                                                 | Example                |
|-----------|--------|----------|-----------------------------------------------------------------------------|------------------------|
| type      | string | No       | Profile type (`App\Models\Gym`, `App\Models\User`). Comma-separated for multiple types | "App\\Models\\Gym,App\\Models\\User" |
| item_id   | int    | No       | Profile ID(s) to filter by (comma-separated for multiple)                    | "1,2,3"               |
| search    | string | No       | Search term for post title or content                                       | "workout"             |
| order     | string | No       | Order of results: `ASC` or `DESC` (default: `DESC`)                         | "DESC"                 |

---

## Response

### 200 OK
Returns a paginated list of post resources.

#### Schema
```json
{
  "data": [
    { /* Post Resource */ }
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
      "profile_type": "App\\Models\\User",
      "profile_id": 42,
      "title": "My Workout",
      "content": "Today I did squats and deadlifts.",
      "is_draft": false
    }
  ],
  "links": {
    "first": "https://api.example.com/api/v1/posts?page=1",
    "last": "https://api.example.com/api/v1/posts?page=10",
    "prev": null,
    "next": "https://api.example.com/api/v1/posts?page=2"
  },
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 10,
    "path": "https://api.example.com/api/v1/posts",
    "per_page": 50,
    "to": 50,
    "total": 500
  }
}
```

For a full schema, see [Post Resource](post_resource.md) and [Pagination Data](../_globals/pagination-data.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../_globals/not-found-errors.md) |
