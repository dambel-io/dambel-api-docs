# `/api/v1/gyms/{gym-id}/subscriptions/checkin/{subscription-id}`
User or gym owner can make a checkin on a subscription.

- Controller: [`App\Http\Controllers\API\V1\Gyms\Subscriptions\CheckInController`](../../../../src/app/Http/Controllers/API/V1/Gyms/Subscriptions\CheckInController.php)
- Method: `POST`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Params

- `notes`: An optional note on the checkin

### Response

201:
```json
<gym subscription checkin resource>
```

[Gym Subscription Checkin Resource](../../resources/gym_subscription_checkin.md)

404: if gym or gym subscription ID is wrong or is inactive

400: if there is an already open checkin that is not checked out yet

403: attempting to checkin on a subscription that user has not permission to or gym is inactive ([Permission error](../../permission-errors.md))

401: [Authentication error](../../authentication-errors.md)

422: [Validation error](../../validation-errors.md)
