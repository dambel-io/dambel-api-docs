# `GET /api/v1/training/services`
You can get list of the training services of a user using this API.


## Params

- `user_id`: to specify the user (can assign multiple by separating ids using `,`)
- `search`: to search based on title and description
- `page`: specify the data page
- `sort`: use `asc` to see oldest and `desc` to latest. Default is `desc`

> Note: The results are firstly sorted based on marketing boosts, the `sort` logic will be applied on the second level

## Response

### 200 OK

```json
{
    "data": [<training service resource>, ...],
    "links": {<pagination data>},
    "meta": {<pagination data>},
}
```

[Training Service Resource](training_service_resource.md)

[Pagination Data](../../_globals/pagination-data.md) (per page: 50)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)
