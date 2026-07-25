# POST /api/v1/ai/threads/{thread-id}/messages/{message-id}/tool-confirmations

Approves or denies a pending AI tool action on a message that paused with `status: "pending_confirmation"` during an interactive run.


---

## Permissions
| Permission                  | Description                |
|-----------------------------|---------------------------|
| `ai_thread_messages.create` | Resolve confirmations in your own thread |

---

## URL Parameters
| Name       | Type | Required | Description                          | Example |
|------------|------|----------|--------------------------------------|---------|
| thread-id  | int  | Yes      | ID of the thread                     | 123     |
| message-id | int  | Yes      | ID of the paused assistant message   | 456     |

---

## Request Body Parameters
| Name     | Type    | Required | Description                                   | Example |
|----------|---------|----------|-----------------------------------------------|---------|
| approved | boolean | Yes      | `true` executes the pending tool call; `false` skips it (the AI is told the user declined) | true |

---

## Request Example
```json
{
  "approved": true
}
```

---

## Response

### 201 Created
Returns the run's next state. `responseMessage` is either the final assistant message (`status: "completed"`) or the same message paused again on another confirmation-required tool call (`status: "pending_confirmation"`).

#### Example
```json
{
  "responseMessage": { /* ai thread message resource */ }
}
```

For a full schema, see [AI Thread Message Resource](../ai_thread_message_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 422    | Validation error, or the message has no pending action to confirm | [Validation error](../../../../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../../../_globals/permission-errors.md) |
| 404    | Thread or message not found, or message not in thread | [Not found error](../../../../_globals/not-found-errors.md) |
