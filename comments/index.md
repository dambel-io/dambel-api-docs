# `GET /api/v1/comments`
You can search the comments using this API. This can be used for both admin management and also getting comments for a specific profile using filters.


## Permissions

- `comments.view`: view your own comments and comments on any public commentable
- `comments.view_any`: view all of the comments even in draft mode on any profile

## Params

- `type`: The commentable type (`App\Models\Gym`, `App\Models\Post`). Can be multiple using `,` separator
- `item_id`: Id of the commentable. Can be multiple using `,` separator
- `user_id`: Id of the user. Can be multiple using `,` separator
- `search`: Search the comments based on content
- `order`: Order of the results. `ASC` or `DESC`. Default is `DESC` so they are sorted by newest

## Response

### 200 OK

```json
{
    "data": [
        {<comment resource>},
        {<comment resource>},
        {<comment resource>},
        {<comment resource>}
    ],
    "links": {<pagination data>},
    "meta": {<pagination data>},
}
```

[Comment Resource](comment_resource.md)

[Pagination Data](../_globals/pagination-data.md) (per page: 50)

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../_globals/not-found-errors.md)
