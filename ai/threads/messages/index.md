# GET /api/v1/ai/threads/{thread-id}/messages

Retrieves a list of messages in a specific AI thread, with support for pagination.


---

## Permissions
| Permission              | Description                |
|-------------------------|---------------------------|
| `ai_thread_messages.view` | View your own thread messages |

---

## URL Parameters
| Name       | Type | Required | Description                | Example |
|------------|------|----------|----------------------------|---------|
| thread-id  | int  | Yes      | ID of the thread           | 123     |

---

## Query Parameters
| Name | Type | Required | Description                | Example |
|------|------|----------|----------------------------|---------|
| page | int  | No       | Page number for pagination | 1       |

---

## Request Example
```
GET /api/v1/ai/threads/123/messages?page=1
Authorization: Bearer {token}
```

---

## Response

### 200 OK
Returns a paginated list of AI thread message resources.

Ordered **newest first**, by `created_at` descending and then by `id` descending. The second key is not cosmetic: `created_at` has one-second resolution, so a user message and the assistant reply it triggers routinely share a timestamp, and `id` is what puts them in the order they were written.

Only `user` and `assistant` messages are returned. The `system` rows the engine writes — the thread's instruction prompt and every tool result — are internal and never listed.

#### Example
```json
{
  "data": [ { /* ai thread message resource */ }, ... ],
  "links": { /* pagination data */ },
  "meta": { /* pagination data */ }
}
```

For a full schema, see [AI Thread Message Resource](ai_thread_message_resource.md) and [Pagination Data](../../../_globals/pagination-data.md) (per page: 100).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../../_globals/permission-errors.md) |
