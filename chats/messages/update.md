# `PUT /api/v1/chats/{chat-id}/messages/{message-id}`
You can update a message using this API.


## Permissions

- `chat_messages.update`: update your own messages

## Params

- `content`: Content of the message

## Response

### 200 OK

```json
<chat message resource>
```

[Chat Message Resource](chat_message_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
