# `POST /api/v1/chats`
You can create a chat using this API.


## Permissions

- `chats.create`: To start a chat

## Params

- `users`: An array of user ids

## Response

### 201 Created
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
