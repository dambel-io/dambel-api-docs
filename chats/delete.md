# DELETE /api/v1/chats/{chat-id}

Deletes a specific chat.


---

## Permissions
| Permission     | Description         |
|----------------|---------------------|
| `chats.delete` | Delete your own chats |

---

## URL Parameters
| Name    | Type | Required | Description                | Example |
|---------|------|----------|----------------------------|---------|
| chat-id | int  | Yes      | ID of the chat to delete   | 123     |

---

## Request Example
```
DELETE /api/v1/chats/123
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
  "message": "Chat deleted successfully."
}
```

Localized from `messages.chats.deleted_successfully` (`fa`: “چت با موفقیت حذف شد.”).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../_globals/not-found-errors.md) |
