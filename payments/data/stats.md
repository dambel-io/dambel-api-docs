# GET /api/v1/payments/data/stats

Receive total stats of payments and transactions in the given date range and filters.


---

## Permissions
| Permission         | Description                              |
|--------------------|------------------------------------------|
| `payments.view_all`| View data of all payments in the system  |
| `payments.view_own`| View only own payment data               |

---

## Query Parameters
| Name         | Type    | Required | Description                                                      | Example                |
|--------------|---------|----------|------------------------------------------------------------------|------------------------|
| type         | string  | No       | [See available types](../payment_resource.md#type). Comma-separated | "wallet,subscription" |
| payable_type | string  | No       | Filter by payable type(s), comma-separated                       | "gym,plan"            |
| payable_id   | int     | No       | Filter by payable ID(s), comma-separated                         | "1,2,3"               |
| user_id      | int     | No       | Filter by user ID(s), comma-separated                            | "10,20"               |
| is_done      | bool    | No       | Filter by completion status                                      | true                   |
| start_date   | string  | No       | Start of date range (YYYY-MM-DD)                                 | "2024-01-01"          |
| end_date     | string  | No       | End of date range (YYYY-MM-DD)                                   | "2024-01-31"          |
| min_amount   | number  | No       | Minimum amount                                                   | 100                    |
| max_amount   | number  | No       | Maximum amount                                                   | 1000                   |
| description  | string  | No       | Search in description                                            | "membership"          |

---

## Request Example
```
GET /api/v1/payments/data/stats?type=income&user_id=10
Authorization: Bearer {token}
```

---

## Response

### 200 OK
Returns stats for each type of payment record.

#### Example
```json
{
  "total_income": 123,
  "total_commission": 123,
  "total_deposit": 123,
  "total_withdrawal": 123,
  "total_purchase": 123,
}
```

Normal users can use this as a overall payment report for their own account, and admins can use it as the whole system cash flow stats.
For example the total amount of commissions, would be the total income of the application.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
