# Insufficient Balance Errors

Describes the structure of the error response when an action costs more than the user's wallet balance (HTTP 400).

---

## Error Response

Every endpoint that spends from the wallet — withdrawal, premium purchase, boost, buying a training service,
subscribing to a gym plan — refuses with a `400` status code and this body when the balance does not cover the cost:

```json
{
  "error": "Insufficient balance.",
  "code": "insufficient_balance",
  "balance": 30000,
  "required_amount": 50000,
  "shortfall": 20000
}
```

| Field | Type | Description |
|---|---|---|
| `error` | string | Localized message (see [Localization](localization.md)). |
| `code` | string | Always `insufficient_balance`. Key on this, not on the text. |
| `balance` | number | The user's current spendable balance, in Tooman (pending withdrawals already deducted). |
| `required_amount` | number | What the action costs, in Tooman. |
| `shortfall` | number | `required_amount - balance`, never negative — the amount to deposit for the action to succeed. |

`POST /payments/boost` additionally repeats the message under `message`, which is the key that endpoint used
before `error` became the shared one.

---

## Manual enrolments never return this error

`POST /training/trainees` called by the trainer, and `POST /gyms/{gym-id}/subscriptions/manage`, book the platform
commission against the trainer's / gym owner's wallet **without** checking it first: a short wallet must not stop
them from taking on a client. The balance is allowed to go negative and is settled by the next deposit.
