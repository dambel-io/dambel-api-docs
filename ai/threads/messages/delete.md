# `DELETE /api/v1/ai/threads/{thread-id}/messages/{message-id}`
You can delete an AI thread message using this API.
Any message after the specified message will be deleted to as these messages are a chain.


## Permissions

- `ai_thread_messages.delete`: To delete your own thread messages

## Response

### 204 No Content
AI Thread Message deleted.

### 401 Unauthorized
[Authentication error](../../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../../_globals/permission-errors.md)

### 404 Not Found
[Not found error](../../../_globals/not-found-errors.md)
