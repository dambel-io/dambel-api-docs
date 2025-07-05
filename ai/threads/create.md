# `POST /api/v1/ai/threads`
You can create an AI thread using this API.


## Permissions

- `ai_threads.create`: To create threads

## Params

- `title`: Optional title
- `anchor_type`: Optional anchor type
- `anchor_id`: Optional anchor ID

## Response

### 201 Created
```json
<ai thread resource>
```

[Ai Thread Resource](ai_thread_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
