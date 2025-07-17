# GET /api/v1/auth/me

Returns information about the currently authenticated user.


---

## Request Parameters
This endpoint does not accept any parameters.

---

## Request Example
```
GET /api/v1/auth/me
Authorization: Bearer {token}
```

---

## Response

### 200 OK
Returns the user resource and a list of permissions.

#### Example
```json
{
  "data": { /* user resource */ },
  "permissions": ["permission 1", "permission 2"]
}
```

For a full schema, see [User Resource](../users/user_resource.md).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |

