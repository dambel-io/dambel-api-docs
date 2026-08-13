# PUT /api/v1/payments/withdrawal/{payment}

Records an operator's decision on a withdrawal request: whether the payout has been transferred, and
whether the request is rejected.

The two are independent. **`is_done` records only that the money reached the user's bank account** — it
has no effect on the user's balance, because a withdrawal holds its amount from the moment it is created
(see [How the balance is computed](../../payments.md#how-the-balance-is-computed)). **The hold is
controlled by `rejected_at`**, which this endpoint sets and clears via `is_rejected`. Rejecting a
withdrawal returns the held amount to the user's spendable balance while keeping the row and its history.


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
| is_done     | boolean | Yes      | Whether the payout has been transferred to the user's bank account | true |
| is_rejected | boolean | No       | Reject the request and release the held amount; clears the rejection when `false`. Omit to leave the current rejection state untouched | true |
| description | string  | No       | Update withdrawal description               | "Updated note" |

---

## Request Example
```json
{
  "is_done": true,
  "description": "Updated note"
}
```

### Reject a request
Releases the hold and returns the amount to the user's spendable balance.

```json
{
  "is_done": false,
  "is_rejected": true
}
```

### Undo a rejection
Re-applies the hold. This can push a balance negative if the user spent the released funds in the
meantime — it is an operator reversing their own decision, and is permitted deliberately so a rejected
row is never stuck.

```json
{
  "is_done": false,
  "is_rejected": false
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
    "rejected_at": null,
    "created_at": "2026-01-01T00:00:00.000000Z"
  }
}
```

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 404    | Withdrawal not found, or the payment is not of type `withdrawal` | N/A            |
| 422    | Validation error — including `is_done: true` on a rejected withdrawal (see below) | [Validation error](../_globals/validation-errors.md) |
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |

#### Completing a rejected withdrawal
A rejected withdrawal was never paid out, so it cannot be marked completed. Both
`{"is_done": true, "is_rejected": true}` and `{"is_done": true}` against a row whose `rejected_at` is
already set return 422 naming `is_done`, and leave the row untouched:

```json
{
  "errors": {
    "is_done": ["A rejected withdrawal cannot be marked as completed."]
  }
}
```

To pay out a request that was previously rejected, un-reject and complete it in the same call:
`{"is_done": true, "is_rejected": false}`.
