# POST /api/v1/chats

Creates a new chat with the specified users.


---

## Permissions
| Permission     | Description         |
|----------------|---------------------|
| `chats.create` | Start a new chat    |

---

## Request Body Parameters
| Name  | Type   | Required | Description                | Example         |
|-------|--------|----------|----------------------------|-----------------|
| users | array  | Yes      | Array of user IDs          | [1, 2, 3]       |

---

## Request Example
```json
{
  "users": [1, 2, 3]
}
```

---

## Response

### 200 OK
Returns the created chat resource.

#### Example
```json
{
  "data": { /* chat resource */ }
}
```

For a full schema, see [Chat Resource](chat_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 422    | Validation error           | [Validation error](../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../_globals/permission-errors.md) |
