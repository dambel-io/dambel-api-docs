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

## How the balance is computed

The returned figure is the **spendable** balance, and it is type-aware — see
[Payment System § How the balance is computed](../../payments.md#how-the-balance-is-computed) for the
full table.

The point clients most often get wrong: **pending withdrawal requests are already subtracted here.** A
withdrawal reduces this number from the moment it is created, not when an admin marks it `is_done`. A
client that subtracts its own pending withdrawals from this value will double-count them.

---

### Error Responses
| Status | Description                | Reference                                                    |
|--------|----------------------------|--------------------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 403    | Forbidden                  | [Permission error](../_globals/permission-errors.md)         |
