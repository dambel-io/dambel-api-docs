# Pagination Data

Describes the structure of pagination metadata returned in paginated API responses.

For more details, see the [Laravel official documentation](https://laravel.com/docs/11.x/eloquent-resources#pagination).

---

## Schema
| Field         | Type    | Description                                 |
|-------------- |---------|---------------------------------------------|
| current_page  | int     | Current page number                         |
| from          | int     | Index of the first item on the current page |
| last_page     | int     | Last page number                            |
| per_page      | int     | Number of items per page                    |
| to            | int     | Index of the last item on the current page  |
| total         | int     | Total number of items                       |
| links         | array   | Pagination navigation links                 |

> **Links carry `page` and nothing else.** They are not a way to re-run a filtered request: none of
> the caller's own query parameters is echoed back into them, so paging a filtered or searched list
> means re-sending the filter alongside `page`. This holds for the Scout-backed searches too —
> `App\Search\ScoutPagination` strips the `query` key Scout's own paginator would otherwise add,
> so a search's links look exactly like an unfiltered listing's.

---

## Example
```json
{
  "current_page": 1,
  "from": 1,
  "last_page": 10,
  "per_page": 30,
  "to": 30,
  "total": 300,
  "links": [ /* ... */ ]
}
```
