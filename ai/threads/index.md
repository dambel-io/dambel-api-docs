# `GET /api/v1/ai/threads`
You can get list of your own threads with AI using this API.


## Permissions

- `ai_threads.view`: To view threads

## Params

- `search`: Search by title
- `anchor_type`: Filter by anchor type (can be multiple separated by `,`)
- `anchor_id`: Filter by anchor ID (can be multiple separated by `,`)
- `sort`: Sort by `desc` or `asc` (default `desc`)
- `page`: Specify the page for pagination

## Response

### 200 OK


```json
{
    "data": [
        {<ai thread resource>},
        {<ai thread resource>},
    ],
    "links": {<pagination data>},
    "meta": {<pagination data>},
}
```

[Ai Thread Resource](ai_thread_resource.md)

[Pagination Data](../../_globals/pagination-data.md) (per page: 50)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
