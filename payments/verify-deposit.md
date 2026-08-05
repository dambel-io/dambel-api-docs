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

### Error Responses
You get redirected to the app URL.

Error message will be shown in the app.
