# `GET /api/v1/chats/{chat-id}/messages`
You can get list of the messages of a chat using this API.


## Permissions

- `chat_messages.view`: to view messages

## Params

- `search`: To search based on text
- `user_id`: To filter by user (multiple using `,` separator)

## Response

### 200 OK

```json
{
    "data": [<chat message resource>, ...],
    "links": {<pagination data>},
    "meta": {<pagination data>}
}
```

[Chat Message Resource](chat_message_resource.md)

> Note: the `unread_count` field on the chat will get updated automatically after getting list of the latest messages

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)
