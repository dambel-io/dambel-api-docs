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

[Gym Subscription Resource](gym_subscription.md)

### 404 Not Found
[If gym not found](../../_globals/not-found-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)
