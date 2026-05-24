# DELETE /api/v1/notifications/delete/{notification-id}

Delete a notification for the authenticated user.


---

## Path Parameters
| Name            | Type | Required | Description                                                      | Example |
|-----------------|------|----------|------------------------------------------------------------------|---------|
| notification-id | int  | Yes       | ID of the notification to delete.   | 123     |

---

## Response

### 204 No Content
Returns a confirmation message.

#### Example
```json
{
  "message": "Notification delete successfully"
}
```

---

### Error Responses
| Status | Description                | Reference                                      |
|--------|----------------------------|------------------------------------------------|
| 401    | Unauthorized               | [Authentication error](../_globals/authentication-errors.md) |
| 404    | Not found                  | [Not-found error](../_globals/not-found-errors.md) |
