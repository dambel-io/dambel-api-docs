# `POST /api/v1/ai/threads/{thread-id}/messages`
You can create an AI thread message using this API.


## Permissions

- `ai_thread_messages.create`: To create messages in your own thread

## Params

- `content`: Content of the message (max 5000 characters)
- `state`: You can optionally pass the state data as JSON. State data can be the current form structure and values, currently selected filters in a search page, or some chart and data analyze data. It can be any JSON. It will be created as a separate system prompt

## Response

### 201 Created
```json
{
    "createdMessage": <ai thread message resource>,
    "responseMessage": <ai thread message resource>
}
```

[Ai Thread Message Resource](ai_thread_message_resource.md)

> NOTE: In responseMessage.updated_state you might find the updated state data that you had initially sent

### 422 Unprocessable Entity
[Validation error](../../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../../_globals/permission-errors.md)

### 429 Too Many Requests
This will be returned if user does not have `ai_thread_messages.create_unlimited` permission (premium account) and has exceeded their daily usage limit which is based on token number.
