# `POST /api/v1/gyms/{gym-id}/subscriptions/checkin/{subscription-id}`
User or gym owner can make a checkin on a subscription.


## Params

- `notes`: An optional note on the checkin

## Response

### 201 Created
```json
<gym subscription checkin resource>
```

[Gym Subscription Checkin Resource](../../resources/gym_subscription_checkin.md)

### 404 Not Found
 if gym or gym subscription ID is wrong or is inactive

### 400 Bad Request
 if there is an already open checkin that is not checked out yet

### 403 Forbidden
 attempting to checkin on a subscription that user has not permission to or gym is inactive ([Permission error](../../permission-errors.md))

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 422 Unprocessable Entity
[Validation error](../../validation-errors.md)
