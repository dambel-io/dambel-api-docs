# `/api/v1/gyms/{gym-id}/subscriptions/subscribe/{plan-id}`
You can subscribe the user into a gym plan using this API.

- Method: `POST`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Response

201:
```json
<gym subscription resource>
```

[Gym Subscription Resource](../../resources/gym_subscription.md)

404: if gym or gym plan ID is wrong or is inactive

401: [Authentication error](../../authentication-errors.md)
