# `/api/v1/gyms/{gym-id}/subscriptions/manage`
You can create a subscription for a gym using this API.

- Controller: [`App\Http\Controllers\API\V1\Gyms\Subscriptions\Manage\CreateGymSubscriptionController`](../../../../../src/app/Http/Controllers/API/V1/Gyms/Subscriptions/Manage/CreateGymSubscriptionController.php)
- Method: `POST`
- [Requires Authentication](../../../auth/login.md#how-to-use-api-token)

### Permissions

- `gym_subscriptions.create`: creating subscriptions for your own gyms
- `gym_subscriptions.create_any`: creating subscriptions for any gym

### Params

- `gym_plan_id`: ID of the gym plan
- `user_id`: ID of the user

### Response

201:
```json
<gym subscription resource>
```

[Gym Subscription Resource](../../../resources/gym_subscription.md)

404: Invalid gym id or gym plan id passed

422: [Validation error](../../../validation-errors.md)

401: [Authentication error](../../../authentication-errors.md)

403: [Permission error](../../../permission-errors.md)
