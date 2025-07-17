# POST /api/v1/payments/withdrawal

Creates a withdrawal request for the authenticated user.


---

## Permissions
| Permission           | Description                        |
|----------------------|------------------------------------|
| `payments.view_own`  | Access the payment system          |
| `payments.withdraw`  | Request a withdrawal               |

---

## Request Body Parameters
| Name        | Type    | Required | Description                                 | Example         |
|-------------|---------|----------|---------------------------------------------|-----------------|
| amount      | decimal | Yes      | Amount to withdraw                          | 100.00          |
| description | string  | No       | Description for the request (max 2000 chars)| "For expenses"  |

---

## Request Example
```json
{
  "amount": 100.00,
  "description": "For expenses"
}
```

---

## Response

### 201 Created
Withdrawal request was created successfully.

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 400    | Insufficient balance       | N/A                                            |
| 422    | Validation error           | [Validation error](../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
