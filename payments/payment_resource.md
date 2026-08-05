# Payment Resource

Represents a payment transaction, including its type, amount, status, and associations.


---

## Schema
| Field         | Type    | Description                                      | Example                |
|---------------|---------|--------------------------------------------------|------------------------|
| id            | int     | Unique identifier for the payment                | 123                    |
| user_id       | int     | ID of the user who made the payment              | 123                    |
| type          | string  | Type of payment (see below)                      | "deposit"             |
| amount        | number  | Amount of the payment, in Tooman                 | 100.0                  |
| description   | string  | Description of the payment. A verified deposit has the gateway reference code appended to it | "Top-up\nReference code: 4837261509" |
| payable_type  | string  | Type of the payable resource (e.g., `App\Models\Gym`) | "App\\Models\\Gym"      |
| payable_id    | int     | ID of the payable resource                       | 456                    |
| meta          | object  | Additional metadata (see below)                  | { ... }                |
| is_done       | bool    | Whether the payment is completed                 | true                   |
| created_at    | string  | Creation timestamp (ISO 8601 format)             | "2025-01-01 00:00:00" |
| user          | object  | Full user object (see [User Resource](../users/user_resource.md))              | { ... }                |

---

### Type
The `type` field can be one of the following:
- `deposit`
- `income`
- `purchase`
- `withdrawal`
- `commission`

---

### Meta
Free-form, and only populated for payment types that have something to record. Deposits carry the
gateway fee breakdown from the moment they are created, and gain the gateway's own figures once
verified (see [the gateway fee](../../payments.md#currency-and-the-gateway-fee)):

| Field          | Type   | Description                                                        |
|----------------|--------|--------------------------------------------------------------------|
| amount         | number | Tooman credited — the same figure as the payment's `amount`        |
| gateway_fee    | number | Tooman the user paid on top of `amount`                            |
| payable_amount | number | Tooman the user was charged at the gateway                         |
| track_id       | string | Gateway track ID (after verification)                              |
| ref_number     | string | Gateway reference code (after verification; may be `null`)         |
| card_number    | string | Masked card number (after verification; may be `null`)             |
| paid_at        | string | Payment timestamp reported by the gateway (after verification)     |
| charged_rial   | int    | Amount in **Rial** as the gateway reports it (after verification)   |

```json
{
  "amount": 700000,
  "gateway_fee": 7786,
  "payable_amount": 707786,
  "track_id": "123456789",
  "ref_number": "4837261509",
  "card_number": "1234-****-****-5678",
  "paid_at": "2026-01-01T00:00:00.000Z",
  "charged_rial": 7077860
}
```

---

## Example
```json
{
  "id": 123,
  "user_id": 123,
  "user": {
    "id": 123,
    "username": "jdoe",
    "first_name": "John",
    "last_name": "Doe",
    "created_at": "2025-01-01 00:00:00"
  },
  "type": "deposit",
  "amount": 100.0,
  "description": "Subscription fee",
  "payable_type": "App\\Models\\Gym",
  "payable_id": 456,
  "meta": {},
  "is_done": true,
  "created_at": "2025-01-01 00:00:00"
}
```
