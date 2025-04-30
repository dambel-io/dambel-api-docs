# `PUT /api/v1/mark-read/{notification-id?}`
You can update posts using this API.


## Params

The `notification-id` in the route is optional. If you don't pass it, all of the unread notifications will be marked as read.

## Response

### 200 OK
```json
{
    "message": "Notifications marked as read",
}
```

### 401 Unauthorized
[Authentication error](../_globals/authentication-errors.md)

### 404 Not Found
[Not-found error](../_globals/not-found-errors.md)
