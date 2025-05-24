# `PUT /api/v1/chats/{chat-id}`
You can update chats using this API.


## Permissions

- `chats.update`: To update your own chat

## Params

- `users`: An array of user ids

## Response

### 200 OK
```json
{
    "chat": {<chat resource>},
}
```

[Chat Resource](chat_resource.md)

### 422 Unprocessable Entity
[Validation error](../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)
