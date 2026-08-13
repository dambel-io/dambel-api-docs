# GET /api/v1/payments

Retrieves a list of payments and transactions. Users can view their own records; admins can view all records in the system.


---

## Permissions
| Permission         | Description                        |
|--------------------|------------------------------------|
| `payments.view_all`| View all payments                  |
| `payments.view_own`| View only own payments             |

---

## Query Parameters
| Name         | Type    | Required | Description                                                      | Example                |
|--------------|---------|----------|------------------------------------------------------------------|------------------------|
| type         | string  | No       | [See available types](payment_resource.md#type). Comma-separated | "wallet,subscription" |
| payable_type | string  | No       | Filter by payable type(s), comma-separated                       | "gym,plan"            |
| payable_id   | int     | No       | Filter by payable ID(s), comma-separated                         | "1,2,3"               |
| user_id      | int     | No       | Filter by user ID(s), comma-separated                            | "10,20"               |
| is_done      | bool    | No       | Filter by completion status                                      | true                   |
| is_rejected  | bool    | No       | Filter withdrawals by rejection state                            | true                   |
| start_date   | string  | No       | Start of date range (YYYY-MM-DD)                                 | "2024-01-01"          |
| end_date     | string  | No       | End of date range (YYYY-MM-DD)                                   | "2024-01-31"          |
| min_amount   | number  | No       | Minimum amount                                                   | 100                    |
| max_amount   | number  | No       | Maximum amount                                                   | 1000                   |
| description  | string  | No       | Search in description                                            | "membership"          |
| page         | int     | No       | Page number for pagination                                       | 1                      |
| sort         | string  | No       | Sort order: `desc` or `asc`                                      | "desc"                |

---

## Request Example
```
GET /api/v1/payments?type=income&user_id=10&sort=desc&page=1
Authorization: Bearer {token}
```

---

## Response

### 200 OK
Returns a paginated list of payment resources.

#### Example
```json
{
  "data": [
    { /* payment resource */ },
    { /* payment resource */ }
  ],
  "links": { /* pagination data */ },
  "meta": { /* pagination data */ }
}
```

For a full schema, see [Payment Resource](payment_resource.md).

`withdrawal`-type records additionally carry a `user_balance` field when the viewer holds
`payments.view_all` — the requesting user's current spendable balance, for verifying funds before
processing the withdrawal. It already excludes this withdrawal's own amount, because a withdrawal
holds its amount out of the balance from the moment it is requested. It is absent on other record
types and for viewers without that permission; see
[Payment Resource](payment_resource.md#schema) for exact semantics.

See [Pagination Data](../_globals/pagination-data.md) (per page: 50).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
