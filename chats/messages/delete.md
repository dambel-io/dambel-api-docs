# `DELETE /api/v1/chats/{chat-id}/messages/{message-id}`
You can delete a message from a chat using this API.


## Permissions

- `chat_messages.delete`: to delete your own messages

## Params

No parameter.

## Response

### 204 No Content
No content when chat message gets deleted

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)
