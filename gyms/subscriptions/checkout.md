# POST /api/v1/gyms/{gym-id}/subscriptions/checkout/{subscription-id}

Checks out the last open check-in for a gym subscription.


---

## URL Parameters
| Name            | Type | Required | Description                | Example |
|-----------------|------|----------|----------------------------|---------|
| gym-id          | int  | Yes      | ID of the gym              | 123     |
| subscription-id | int  | Yes      | ID of the subscription     | 456     |

---

## Request Example
```
POST /api/v1/gyms/123/subscriptions/checkout/456
Authorization: Bearer {token}
```

---

## Response

### 200 OK
Returns a success message when checked out successfully.

#### Example
```json
{
  "message": "Checked out successfully"
}
```

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 404    | Not found (invalid gym or subscription, or inactive) |  |
| 400    | No open check-in to check out |  |
| 403    | Forbidden (no permission or gym inactive) | [Permission error](../../_globals/permission-errors.md) |
| 401    | Unauthorized               | [Authentication error](../../_globals/authentication-errors.md) |
