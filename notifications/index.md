# `GET /api/v1/notifications`
Users can get a paginated list of their latest notifications using this API.


## Response

### 200 OK

```json
{
    "data": [
        {<notification resource>},
        {<notification resource>},
        {<notification resource>},
        {<notification resource>}
    ],
    "links": {<pagination data>},
    "meta": {<pagination data>},
}
```

[Notification Resource](notification_resource.md)

[Pagination Data](../_globals/pagination-data.md) (per page: 50)

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)
