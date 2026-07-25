# POST /api/v1/ai/threads/{thread-id}/messages

Creates a new message in a specific AI thread and runs the AI engine to produce a response.


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
| context | string | No       | Screen-context data as a JSON string (read-only for the AI) | "{ ... }" |
| interactive | boolean | No   | Opt into real-time tool-call progress events and tool confirmations (default `false`) | true |
| attachments | file[] | No    | Up to 5 files as multipart uploads | — |
| attachments.* | file | No    | `image/jpeg`, `image/png`, `image/webp`, or `application/pdf`; max 10 MB each | photo.jpg |

Attachments require the request to be sent as `multipart/form-data`; all other fields work in both JSON and multipart encodings. Images are passed to the model as vision input; PDF text is extracted server-side and injected into the conversation.

---

## Request Example
```json
{
  "content": "Hello!",
  "context": "{ \"page\": [\"gymView\", 123], \"form\": { \"field\": \"value\" } }",
  "interactive": true
}
```

Multipart example (with attachments):

```
POST /api/v1/ai/threads/123/messages
Content-Type: multipart/form-data

content=Check out my progress photo
attachments[]=@photo.jpg
attachments[]=@report.pdf
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

- `responseMessage.status` is normally `"completed"`. In an interactive run that hit a confirmation-required tool it is `"pending_confirmation"` — the run is paused and must be resolved via [POST .../tool-confirmations](tool-confirmations/create.md).
- With `interactive: true`, per-tool-call progress events broadcast on the user's private channel while the request is processing — see [Broadcasting](../../../_globals/broadcasting.md) and the `AiToolCallProgress` payload in the [broadcasting docs](../../../../broadcasting.md).
- `responseMessage.updated_context` is deprecated and always `null` for new messages.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 422    | Validation error (including too many attachments, oversized files, or disallowed MIME types) | [Validation error](../../../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../../_globals/permission-errors.md) |
| 429    | AI usage budget exceeded — the user's rolling 24-hour AI spend (USD) reached their tier budget |  |

## AI System
The AI system uses OpenAI APIs behind the scenes. It handles reading Dambel documentation files, searching the web or reading a specific web page, saving memories for each user and accessing them in other chats, reading data from Dambel's database, analyzing attached images and PDF documents, and even reporting the conversation whenever necessary. Once it finishes its tool calls, it returns the final response to the message. Usage is metered by USD spend over a rolling 24-hour window, with separate budgets for free and premium users.
