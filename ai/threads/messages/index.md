# `GET /api/v1/ai/threads/{thread-id}/messages`
You can get list of the messages in a thread using this API.


## Permissions

- `ai_thread_messages.view`: To view your own thread messages

## Params

- `page`: Specify the page for pagination

## Response

### 200 OK


```json
{
    "data": [
        {<ai thread message resource>},
        {<ai thread message resource>},
    ],
    "links": {<pagination data>},
    "meta": {<pagination data>},
}
```

[Ai Thread Message Resource](ai_thread_message_resource.md)

[Pagination Data](../../../_globals/pagination-data.md) (per page: 100)

### 401 Unauthorized
[Authentication error](../../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../../_globals/permission-errors.md)
