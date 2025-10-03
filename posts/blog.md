# GET /api/v1/posts/blog

Retrieves a list of posts, with support for filtering by profile type, profile ID, search, and order. This endpoint is used to retrieve blog posts for the website.


**No authentication required.**

---

## Query Parameters
| Name      | Type   | Required | Description                                                                 | Example                |
|-----------|--------|----------|-----------------------------------------------------------------------------|------------------------|
| search    | string | No       | Search term for post title or content                                       | "workout"             |
| ids    | string | No       | Get specific posts by ID(s)                                       | "1,2"             |
| order     | string | No       | Order of results: `ASC` or `DESC` (default: `DESC`)                         | "DESC"                 |
| per_page     | int | No       | Set the per page count (default: 50)                         | 10                 |

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

For a full schema, see [Post Resource](post_resource.md) and [Pagination Data](../_globals/pagination-data.md).
