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

---

### Error Responses
You get redirected to the app URL.

Error message will be shown in the app.
