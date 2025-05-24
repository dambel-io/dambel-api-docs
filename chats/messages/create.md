# `POST /api/v1/chats/{chat-id}/messages`
You can send a message using this API.


## Permissions

- `chat_messages.create`: to send a message

## Params

- `content`: Message
- `chat_message_id`: Id of the message in case its in reply to it

## Response

### 201 Created
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
