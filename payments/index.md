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
GET /api/v1/payments?type=wallet&user_id=10&sort=desc&page=1
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

See [Pagination Data](../_globals/pagination-data.md) (per page: 30).

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
