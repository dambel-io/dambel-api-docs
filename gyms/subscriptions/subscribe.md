# `POST /api/v1/gyms/{gym-id}/subscriptions/subscribe/{plan-id}`
You can subscribe the user into a gym plan using this API.


## Response

### 201 Created
```json
<gym subscription resource>
```

[Gym Subscription Resource](../../resources/gym_subscription.md)

### 400 Bad Request
When the account balance is not enough to pay for the subscription.

### 404 Not Found
 if gym or gym plan ID is wrong or is inactive

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)
