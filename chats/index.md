# GET /api/v1/chats

Retrieves a list of chats, with support for filtering and pagination. Can be used for both admin management and user chat lists.


---

## Permissions
| Permission   | Description                |
|--------------|----------------------------|
| `chats.view` | View your own chats        |

---

## Request Example
```
GET /api/v1/chats
Authorization: Bearer {token}
```

---

## Response

### 200 OK
Returns a paginated list of chat resources.

#### Example
```json
{
  "data": [ { /* chat resource */ }, ... ],
  "links": { /* pagination data */ },
  "meta": { /* pagination data */ }
}
```

For a full schema, see [Chat Resource](chat_resource.md) and [Pagination Data](../_globals/pagination-data.md) (per page: 50).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
| 404    | Not found                  | [Not-found error](../_globals/not-found-errors.md) |
