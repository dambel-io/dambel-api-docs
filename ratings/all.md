# `GET /api/v1/ratings/all`
You can get all of the ratings as an admin.


## Permissions

- `ratings.view_any`: to view all of the ratings in the system in addition to your own

## Params

- `type`: The ratable type (`App\Models\Gym`, `App\Models\TrainingService`). Can be multiple using `,` separator
- `item_id`: Id of the item. Can be multiple using `,` separator
- `user_id`: Id of the user (The one who rated). Can be multiple using `,` separator
- `from_date`: Start of date range
- `to_date`: End of date range
- `from_score`: Minimum score
- `to_score`: Maximum score
- `order`: Order of the results. `ASC` or `DESC`. Default is `DESC` so they are sorted by newest

## Response

### 200 OK

```json
{
    "data": [
        {<rating resource>},
        {<rating resource>},
        {<rating resource>},
        {<rating resource>}
    ],
    "links": {<pagination data>},
    "meta": {<pagination data>},
}
```

[Rating Resource](../resources/rating.md)

[Pagination Data](../pagination-data.md) (per page: 50)

### 401 Unauthorized
[Authentication error](../authentication-errors.md)

### 403 Forbidden
[Permission error](../permission-errors.md)

### 404 Not Found
[Not-found error](../not-found-errors.md)
