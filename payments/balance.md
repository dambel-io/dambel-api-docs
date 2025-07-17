# GET /api/v1/payments/balance

Retrieves the current balance for the authenticated user.


---

## Permissions
| Permission                | Description                        |
|---------------------------|------------------------------------|
| `payments.view_own`       | Access the payment system          |
| `payments.view_own_balance`| View your own balance              |

---

## Response

### 200 OK
Returns the user's current balance.

#### Example
```json
{
  "balance": 123.456
}
```

---

### Error Responses
| Status | Description                | Reference                                                    |
|--------|----------------------------|--------------------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden                  | [Permission error](../_globals/permission-errors.md)         |
