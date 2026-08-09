# DELETE /api/v1/ai/threads/{thread-id}/messages/{message-id}

Deletes a specific message from an AI thread. Any message after the specified message will also be deleted, as messages are chained.


---

## Permissions
| Permission                  | Description                |
|-----------------------------|---------------------------|
| `ai_thread_messages.delete` | Delete your own thread messages |

---

## URL Parameters
| Name       | Type | Required | Description                | Example |
|------------|------|----------|----------------------------|---------|
| thread-id  | int  | Yes      | ID of the thread           | 123     |
| message-id | int  | Yes      | ID of the message to delete| 456     |

---

## Request Example
```
DELETE /api/v1/ai/threads/123/messages/456
Authorization: Bearer {token}
```

---

## Response

### 204 No Content
Despite the `204`, this endpoint **does** return a JSON body — a localized confirmation message.
HTTP defines `204` as bodyless, so some clients and proxies discard it; treat the body as informational,
not something to depend on.

```json
{
  "message": "AI message deleted successfully."
}
```

Localized from `messages.ai.threads.messages.deleted_successfully` (`fa`: “پیام AI با موفقیت حذف شد.”).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not found error](../../../_globals/not-found-errors.md) |
