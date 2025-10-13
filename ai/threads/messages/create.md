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
| context   | object | No       | Optional context data as JSON | { ... }         |

---

## Request Example
```json
{
  "content": "Hello!",
  "context": { "page": ["gymView", 123], "form": { "field": "value" } }
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

> In `responseMessage.updated_context` you may find the updated context data you initially sent. For example form fields get updated.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 422    | Validation error           | [Validation error](../../../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../../_globals/permission-errors.md) |
| 429    | Too many requests (rate limit exceeded) |  |

## AI System
The AI system uses OpenAI APIs behind the scenes, it handles reading Dambel documentation files, searching web or reading a specific web page, saving memories for each user and access them in other chats, reading data from Dambel's database, and even reporting the conversation whenever necessary. Once it uses every tool that it has, it returns the final response to the message.
