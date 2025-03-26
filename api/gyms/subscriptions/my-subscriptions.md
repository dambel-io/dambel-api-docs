# `/api/v1/gyms/{gym-id}/subscriptions/my-subscriptions`
Users can get their own subscriptions on a specific gym.

- Method: `GET`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Response

200:
```json
[
    <gym subscription resource>,
    <gym subscription resource>...
]
```

[Gym Subscription Resource](../../resources/gym_subscription.md)

404: [If gym not found](../../not-found-errors.md)

401: [Authentication error](../../authentication-errors.md)
