# `GET /api/v1/reports`
You can search the reports using this API. This can be used for both admin management and also getting your own reports.


## Permissions

- `reports.view`: view your own reports
- `reports.view_all`: view all of the reports as an admin

## Params

- `type`: The profile type (e.g. `App\Models\Gym`, `App\Models\User`). Can be multiple using `,` separator
- `item_id`: Id of the reportable. Can be multiple using `,` separator
- `user_id`: Id of the user. Can be multiple using `,` separator
- `search`: Search the reports based on description
- `signed_off`: Boolean
- `order`: Order of the results. `ASC` or `DESC`. Default is `DESC` so they are sorted by newest

## Response

### 200 OK

```json
{
    "data": [
        {<report resource>},
        {<report resource>},
        {<report resource>},
        {<report resource>}
    ],
    "links": {<pagination data>},
    "meta": {<pagination data>},
}
```

[Report Resource](report_resource.md)

[Pagination Data](../_globals/pagination-data.md) (per page: 50)

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../_globals/not-found-errors.md)
