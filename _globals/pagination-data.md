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
