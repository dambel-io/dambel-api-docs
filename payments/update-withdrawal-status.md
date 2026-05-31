# PUT /api/v1/payments/withdrawal/{payment}

Updates the `is_done` status for a withdrawal payment record.


---

## Permissions
| Permission                  | Description                                |
|-----------------------------|--------------------------------------------|
| `payments.view_all`         | Access payments administration              |
| `payments.update_withdrawal`| Update withdrawal completion status        |

---

## Request Body Parameters
| Name        | Type    | Required | Description                                 | Example         |
|-------------|---------|----------|---------------------------------------------|-----------------|
| is_done     | boolean | Yes      | Set withdrawal completion status            | true            |
| description | string  | No       | Update withdrawal description               | "Updated note" |

---

## Request Example
```json
{
  "is_done": true,
  "description": "Updated note"
}
```

---

## Response
### 200 OK
Returns the updated withdrawal payment resource.

```json
{
  "data": {
    "id": 123,
    "user_id": 10,
    "type": "withdrawal",
    "amount": 150.00,
    "description": null,
    "payable_type": null,
    "payable_id": null,
    "meta": null,
    "is_done": true,
    "created_at": "2026-01-01T00:00:00.000000Z"
  }
}
```

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 404    | Withdrawal not found       | N/A                                            |
| 422    | Validation error           | [Validation error](../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
