# `DELETE /api/v1/chats/{chat-id}`
You can delete a chat using this API.


## Permissions

- `chats.delete`: To delete your own chats

## Response

### 204 No Content
No content when chat gets deleted

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../_globals/not-found-errors.md)
