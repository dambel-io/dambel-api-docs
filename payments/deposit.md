# POST /api/v1/payments/deposit

Creates a deposit request for the authenticated user to add funds to their account.


---

## Permissions
| Permission           | Description                        |
|----------------------|------------------------------------|
| `payments.view_own`  | Access the payment system          |
| `payments.deposit`   | Deposit money into own account     |

---

## Request Body Parameters
| Name        | Type    | Required | Description                                 | Example         |
|-------------|---------|----------|---------------------------------------------|-----------------|
| amount      | decimal | Yes      | Amount to deposit                           | 250.00          |
| description | string  | No       | Description for the deposit                 | "Top-up"        |

---

## Request Example
```json
{
  "amount": 250.00,
  "description": "Top-up"
}
```

---

## Response

### 201 Created
Returns a payment gateway link for the user to complete the deposit process.

#### Example
```json
{
  "link": "https://payment-gateway.example.com/redirect/abc123"
}
```

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 400    | Payment process error      | N/A                                            |
| 422    | Validation error           | [Validation error](../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
