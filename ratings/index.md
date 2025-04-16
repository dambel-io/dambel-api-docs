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

[Rating Resource](../resources/rating.md)

[Pagination Data](../pagination-data.md) (per page: 50)

### 401 Unauthorized
[Authentication error](../authentication-errors.md)

### 403 Forbidden
[Permission error](../permission-errors.md)

### 404 Not Found
[Not-found error](../not-found-errors.md)
