# `PUT /api/v1/gyms/{gym-id}/subscriptions/manage/{subscription-id}`
You can update a subscription for a gym using this API.


### Permissions

- `gym_subscriptions.update`: updating subscriptions for your own gyms
- `gym_subscriptions.update_any`: updating subscriptions for any gym

### Params

- `expires_at`: Date
- `available_sessions_count`: Integer

Both parameters are optional and will not be changed if you don't send them. You can also set them to null

### Response

200:
```json
<gym subscription resource>
```

[Gym Subscription Resource](../../../resources/gym_subscription.md)

404: Invalid gym id or gym plan id passed

422: [Validation error](../../../validation-errors.md)

401: [Authentication error](../../../authentication-errors.md)

403: [Permission error](../../../permission-errors.md)
