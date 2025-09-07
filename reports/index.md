# GET /api/v1/reports

Retrieves a list of reports, with support for filtering by type, reportable ID, user, search, signed-off status, and order. Useful for both admin management and fetching your own reports.


---

## Permissions
| Permission         | Description                                 |
|--------------------|---------------------------------------------|
| `reports.view`     | View your own reports                       |
| `reports.view_all` | View all reports as an admin                |

---

## Query Parameters
| Name       | Type    | Required | Description                                                                 | Example                |
|------------|---------|----------|-----------------------------------------------------------------------------|------------------------|
| type       | string  | No       | Profile type (e.g., `App\Models\Gym`, `App\Models\User`). Comma-separated for multiple types | "App\\Models\\Gym,App\\Models\\User" |
| item_id    | int     | No       | Reportable ID(s) to filter by (comma-separated for multiple)                | "1,2,3"               |
| user_id    | int     | No       | User ID(s) to filter by (comma-separated for multiple)                      | "5,6"                 |
| search     | string  | No       | Search term for report description                                          | "broken"              |
| signed_off | bool    | No       | Filter by signed-off status                                                 | true                   |
| ai_marked_spam | bool    | No       | Filter by ai-marked-spam status                                                 | true                   |
| order      | string  | No       | Order of results: `ASC` or `DESC` (default: `DESC`)                         | "DESC"                 |

---

## Response

### 200 OK
Returns a paginated list of report resources.

#### Schema
```json
{
  "data": [
    { /* Report Resource */ }
  ],
  "links": { /* Pagination Data */ },
  "meta": { /* Pagination Data */ }
}
```

For a full schema, see [Report Resource](report_resource.md) and [Pagination Data](../_globals/pagination-data.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../_globals/not-found-errors.md) |
