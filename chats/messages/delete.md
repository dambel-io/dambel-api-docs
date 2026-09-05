# DELETE /api/v1/chats/{chat-id}/messages/{message-id}

Deletes a specific message from a chat.


---

## Permissions
| Permission           | Description                |
|----------------------|---------------------------|
| `chat_messages.delete` | Delete your own messages  |

---

## URL Parameters
| Name       | Type | Required | Description                | Example |
|------------|------|----------|----------------------------|---------|
| chat-id    | int  | Yes      | ID of the chat             | 123     |
| message-id | int  | Yes      | ID of the message to delete| 456     |

---

## Request Example
```
DELETE /api/v1/chats/123/messages/456
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
  "message": "Message deleted successfully."
}
```

Localized from `messages.chats.messages.deleted_successfully` (`fa`: “پیام با موفقیت حذف شد.”).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../../_globals/not-found-errors.md) |

`{message}` must belong to `{chat}`. A message id from another chat returns **404**, not 403 — a 403 would
confirm to the caller that the message exists.

