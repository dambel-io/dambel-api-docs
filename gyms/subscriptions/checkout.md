# `POST /api/v1/gyms/{gym-id}/subscriptions/checkout/{subscription-id}`
User or gym owner can checkout the last opened checkin on a subscription.


## Response

### 200 OK

```json
{
    "message": "Checked out successfully"
}
```

### 404 Not Found
 if gym or gym subscription ID is wrong or is inactive

### 400 Bad Request
 if there is no open checkin to be checked out

### 403 Forbidden
 attempting to checkout on a subscription that user has not permission to or gym is inactive ([Permission error](../../_globals/permission-errors.md))

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)
