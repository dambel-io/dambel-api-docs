# `POST /api/v1/gyms/{gym-id}/subscriptions/manage`
You can create a subscription for a gym using this API.


## Permissions

- `gym_subscriptions.create`: creating subscriptions for your own gyms
- `gym_subscriptions.create_any`: creating subscriptions for any gym

## Params

- `gym_plan_id`: ID of the gym plan
- `user_id`: ID of the user

## Response

### 201 Created
```json
<gym subscription resource>
```

[Gym Subscription Resource](../gym_subscription.md)

### 404 Not Found
 Invalid gym id or gym plan id passed

### 422 Unprocessable Entity
[Validation error](../../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../../_globals/permission-errors.md)
