# `GET /api/v1/ratings`
You can get your OWN ratings using this API.


## Params

Same as [`/all`](all.md#params).

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

[Rating Resource](rating_resource.md)

[Pagination Data](../_globals/pagination-data.md) (per page: 50)

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../_globals/not-found-errors.md)
