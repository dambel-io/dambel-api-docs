# `DELETE /api/v1/ai/threads/{thread-id}`
You can delete an AI thread using this API.


## Permissions

- `ai_threads.delete`: To delete your own threads

## Response

### 204 No Content
AI Thread deleted.

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not found error](../../_globals/not-found-errors.md)
