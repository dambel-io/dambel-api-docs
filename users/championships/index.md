# `GET /api/v1/users/{user-id}/championships`

Retrieve a list of championships for a user.


---

## Permissions
| Permission                | Description                                 |
|---------------------------|---------------------------------------------|
| `championships.view`      | View your own championships                 |
| `championships.view_any`  | View championships for any user             |

---

## Response

### 200 OK
```
{
  "data": [<championship resource>, ...]
}
```
- [Championship Resource](championship_resource.md)

---

## Error Responses
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)
- **404 Not Found:** [Not-found error](../../_globals/not-found-errors.md)

---
