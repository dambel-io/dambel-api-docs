# `GET /api/v1/posts`
You can search the posts using this API. This can be used for both admin management and also getting posts for a specific profile using filters.


## Permissions

- `posts.view`: view your own posts and posts on any public profile
- `posts.view_any`: view all of the posts even in draft mode on any profile

## Params

- `type`: The profile type (`App\Models\Gym`, `App\Models\User`). Can be multiple using `,` separator
- `item_id`: Id of the profile. Can be multiple using `,` separator
- `search`: Search the posts based on title and content
- `order`: Order of the results. `ASC` or `DESC`. Default is `DESC` so they are sorted by newest

## Response

### 200 OK

```json
{
    "data": [
        {<post resource>},
        {<post resource>},
        {<post resource>},
        {<post resource>}
    ],
    "links": {<pagination data>},
    "meta": {<pagination data>},
}
```

[Post Resource](post_resource.md)

[Pagination Data](../_globals/pagination-data.md) (per page: 50)

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../_globals/not-found-errors.md)
