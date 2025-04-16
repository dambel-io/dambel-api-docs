# `GET /api/v1/gyms/{gym-id}/subscriptions/my-subscriptions`
Users can get their own subscriptions on a specific gym.


## Response

### 200 OK

```json
[
    <gym subscription resource>,
    <gym subscription resource>...
]
```

[Gym Subscription Resource](../../resources/gym_subscription.md)

### 404 Not Found
[If gym not found](../../not-found-errors.md)

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)
