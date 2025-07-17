# `GET /api/v1/users/{user-id}/education`

Retrieve a list of education records for a user.


---

## Permissions
| Permission           | Description                                 |
|----------------------|---------------------------------------------|
| `education.view`     | View your own education records             |
| `education.view_any` | View education records for any user         |

---

## Response

### 200 OK
```
{
  "data": [<education resource>, ...]
}
```
- [Education Resource](education_resource.md)

---

## Error Responses
- **401 Unauthorized:** [Authentication error](../../_globals/authentication-errors.md)
- **403 Forbidden:** [Permission error](../../_globals/permission-errors.md)
- **404 Not Found:** [Not-found error](../../_globals/not-found-errors.md)

---
