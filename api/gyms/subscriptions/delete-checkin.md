# `DELETE /api/v1/gyms/{gym-id}/subscriptions/delete-checkin/{subscription-id}/{checkin-id}`
You can delete a checkin on a gym subscription for a gym using this API.


## Permissions

- `gym_subscription_checkins.delete`: deleting checkins for your own gyms
- `gym_subscription_checkins.delete_any`: deleting checkins for any gym

## Response

### 204 No Content
 Deleted successfully

### 404 Not Found
 Invalid gym id, subscription id, or checkin id passed

### 401 Unauthorized
 [Authentication error](../../authentication-errors.md)

### 403 Forbidden
 [Permission error](../../permission-errors.md)
