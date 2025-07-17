# PUT /api/v1/mark-read/{notification-id?}

Marks one or all notifications as read for the authenticated user. If `notification-id` is omitted, all unread notifications will be marked as read.


---

## Path Parameters
| Name            | Type | Required | Description                                                      | Example |
|-----------------|------|----------|------------------------------------------------------------------|---------|
| notification-id | int  | No       | ID of the notification to mark as read. If omitted, marks all.   | 123     |

---

## Response

### 200 OK
Returns a confirmation message.

#### Example
```json
{
  "message": "Notifications marked as read"
}
```

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 404    | Not found                  | [Not-found error](../_globals/not-found-errors.md) |
