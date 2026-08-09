# DELETE /api/v1/ai/threads/{thread-id}

Deletes a specific AI thread.


---

## Permissions
| Permission        | Description                |
|-------------------|---------------------------|
| `ai_threads.delete` | Delete your own threads   |

---

## URL Parameters
| Name       | Type | Required | Description                | Example |
|------------|------|----------|----------------------------|---------|
| thread-id  | int  | Yes      | ID of the thread to delete | 123     |

---

## Request Example
```
DELETE /api/v1/ai/threads/123
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
  "message": "AI thread deleted successfully."
}
```

Localized from `messages.ai.threads.deleted_successfully` (`fa`: “موضوع AI با موفقیت حذف شد.”).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not found error](../../_globals/not-found-errors.md) |
