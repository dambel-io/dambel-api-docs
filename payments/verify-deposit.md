# GET /api/v1/payments/verify-deposit/{deposit-id}

Callback endpoint for the Zibal payment gateway to verify a deposit transaction.


---

## URL Parameters
| Name        | Type | Required | Description                | Example |
|-------------|------|----------|----------------------------|---------|
| deposit-id  | int  | Yes      | ID of the deposit to verify | 123     |

---

## Query Parameters
| Name      | Type   | Required | Description                        | Example     |
|-----------|--------|----------|------------------------------------|-------------|
| trackId   | string | Yes      | Track ID from Zibal                | "123456789" |
| success   | string | Yes      | Payment result from Zibal (`"1"` = success, `"0"` = failed) | `"1"` |

---

## Request Example
```
GET /api/v1/payments/verify-deposit/123?trackId=123456789&success=1
```

---

## Response

### 200 OK
Deposit was successfully verified.

You get redirected to the app URL.

On a successful verification the deposit record is finalized (`is_done` becomes `true`) and the
gateway's reference code is stored in two places:

- appended to the payment's `description` as a localized line (`Reference code: …` /
  `کد پیگیری: …`), so the user can read it wherever the payment is listed
- in `meta`, alongside the track ID, masked card number, payment time and the Rial amount the
  gateway charged — merged into the fee breakdown already stored when the deposit was created

A repeated callback never appends the reference code twice.

---

### When a callback is refused

This route is public and unauthenticated — both the payment ID and `trackId` arrive from the
outside world — so a callback is finalized only when all of the following hold. Every refusal
redirects to the app URL exactly like a failed payment: the outcomes are deliberately
indistinguishable to the caller, so none of them can be used to probe another user's payments.

| Condition | Behaviour |
|---|---|
| `success` is not `1` | Refused; the deposit stays unfinalized. |
| The payment is already `is_done` | Short-circuits before the gateway is contacted. A replayed callback cannot credit the balance twice. |
| `trackId` does not equal the `track_id` recorded on the payment when it was created | Refused. A payment with no recorded `track_id` is refused outright. |
| The gateway's settled amount does not equal the payment's gross amount (amount + gateway fee) | Refused. This stops a `trackId` from a smaller settled charge finalizing a larger deposit. |

The two track-ID values and the settlement amounts are gateway-sensitive and are deliberately
kept out of the logs.

---

### Error Responses
You get redirected to the app URL.

Error message will be shown in the app.
