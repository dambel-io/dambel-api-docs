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
