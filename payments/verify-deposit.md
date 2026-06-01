# GET /api/v1/payments/verify-deposit/{deposit-id}

Callback endpoint for payment service providers to verify a deposit transaction.


---

## URL Parameters
| Name        | Type | Required | Description                | Example |
|-------------|------|----------|----------------------------|---------|
| deposit-id  | int  | Yes      | ID of the deposit to verify | 123     |

---

## Query Parameters
| Name      | Type   | Required | Description                        | Example     |
|-----------|--------|----------|------------------------------------|-------------|
| Authority | string | Yes      | Authority code from PSP            | "A0000001" |
| Status    | string | Yes      | Status from PSP                    | "OK"       |

---

## Request Example
```
GET /api/v1/payments/verify-deposit/123?Authority=A0000001&Status=OK
```

---

## Response

### 200 OK
Deposit was successfully verified.

#### Example
```json
{
  "message": "Deposit successful",
  "payment": {
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
    "payable_type": null,
    "payable_id": null,
    "meta": {},
    "is_done": true,
    "created_at": "2025-01-01 00:00:00"
  }
}
```

For a full schema, see [Payment Resource](payment_resource.md).

---

### Error Responses
| Status | Description                | Example/Reference                                      |
|--------|----------------------------|--------------------------------------------------------|
| 400    | Payment failed             | `{ "error": "..." }`                                  |
