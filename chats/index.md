# `GET /api/v1/chats`
You can search the chats using this API. This can be used for both admin management and also getting chats for a specific profile using filters.


## Permissions

- `chats.view`: view your own chats

## Response

### 200 OK

```json
{
    "data": [
        {<chat resource>},
        {<chat resource>},
        {<chat resource>},
        {<chat resource>}
    ],
    "links": {<pagination data>},
    "meta": {<pagination data>},
}
```

[Chat Resource](chat_resource.md)

[Pagination Data](../_globals/pagination-data.md) (per page: 50)

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../_globals/not-found-errors.md)
