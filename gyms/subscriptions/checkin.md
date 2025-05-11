# `POST /api/v1/gyms/{gym-id}/subscriptions/checkin/{subscription-id}`
User or gym owner can make a checkin on a subscription.


## Permissions

- `gym_subscriptions.checkin`: for gym admin to do the checkin for user

## Params

- `notes`: An optional note on the checkin

## Response

### 201 Created
```json
<gym subscription checkin resource>
```

[Gym Subscription Checkin Resource](gym_subscription_checkin_resource.md)

### 404 Not Found
 if gym or gym subscription ID is wrong or is inactive

### 400 Bad Request
 if there is an already open checkin that is not checked out yet

### 403 Forbidden
 attempting to checkin on a subscription that user has not permission to or gym is inactive ([Permission error](../../_globals/permission-errors.md))

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)
