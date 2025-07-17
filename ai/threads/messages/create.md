# POST /api/v1/ai/threads/{thread-id}/messages

Creates a new message in a specific AI thread.


---

## Permissions
| Permission                  | Description                |
|-----------------------------|---------------------------|
| `ai_thread_messages.create` | Create messages in your own thread |

---

## URL Parameters
| Name       | Type | Required | Description                | Example |
|------------|------|----------|----------------------------|---------|
| thread-id  | int  | Yes      | ID of the thread           | 123     |

---

## Request Body Parameters
| Name    | Type   | Required | Description                | Example         |
|---------|--------|----------|----------------------------|-----------------|
| content | string | Yes      | Content of the message (max 5000 chars) | "Hello!" |
| state   | object | No       | Optional state data as JSON | { ... }         |

---

## Request Example
```json
{
  "content": "Hello!",
  "state": { "form": { "field": "value" } }
}
```

---

## Response

### 201 Created
Returns the created message and the AI's response message.

#### Example
```json
{
  "createdMessage": { /* ai thread message resource */ },
  "responseMessage": { /* ai thread message resource */ }
}
```

For a full schema, see [AI Thread Message Resource](ai_thread_message_resource.md).

> In `responseMessage.updated_state` you may find the updated state data you initially sent.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 422    | Validation error           | [Validation error](../../../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../../_globals/permission-errors.md) |
| 429    | Too many requests (rate limit exceeded) |  |
