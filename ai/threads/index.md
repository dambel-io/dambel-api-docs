# GET /api/v1/ai/threads

Retrieves a list of your AI threads, with support for filtering and pagination.


---

## Permissions
| Permission      | Description                |
|-----------------|---------------------------|
| `ai_threads.view` | View your own threads     |

---

## Query Parameters
| Name        | Type   | Required | Description                                 | Example         |
|-------------|--------|----------|---------------------------------------------|-----------------|
| search      | string | No       | Search by title                             | "project"      |
| sort        | string | No       | Sort order: `desc` or `asc` (default `desc`)| "desc"         |
| page        | int    | No       | Page number for pagination                  | 1               |

---

## Request Example
```
GET /api/v1/ai/threads?search=project&sort=desc&page=1
Authorization: Bearer {token}
```

---

## Response

### 200 OK
Returns a paginated list of AI thread resources.

#### Example
```json
{
  "data": [ { /* ai thread resource */ }, ... ],
  "links": { /* pagination data */ },
  "meta": { /* pagination data */ }
}
```

For a full schema, see [AI Thread Resource](ai_thread_resource.md) and [Pagination Data](../../_globals/pagination-data.md) (per page: 50).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
