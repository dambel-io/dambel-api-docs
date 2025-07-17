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
No content is returned when the thread is successfully deleted.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
| 404    | Not found                  | [Not found error](../../_globals/not-found-errors.md) |
