# POST /api/v1/ai/threads

Creates a new AI thread.


---

## Permissions
| Permission        | Description                |
|-------------------|---------------------------|
| `ai_threads.create` | Create new threads        |

---

## Request Body Parameters
| Name        | Type   | Required | Description                                 | Example         |
|-------------|--------|----------|---------------------------------------------|-----------------|
| title       | string | No       | Optional title for the thread               | "My Thread"     |
| context_type | string | No       | Optional context type                        | "plan"          |
| context_id   | int    | No       | Optional context ID                          | 42              |

---

## Request Example
```json
{
  "title": "My Thread",
  "context_type": "plan",
  "context_id": 42
}
```

---

## Response

### 201 Created
Returns the created AI thread resource.

#### Example
```json
{ /* ai thread resource */ }
```

For a full schema, see [AI Thread Resource](ai_thread_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 422    | Validation error           | [Validation error](../../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
| 403    | Forbidden (no permission)  | [Permission error](../../_globals/permission-errors.md) |
