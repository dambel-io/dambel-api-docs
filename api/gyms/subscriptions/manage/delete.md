# `DELETE /api/v1/gyms/{gym-id}/subscriptions/manage/{subscription-id}`
You can delete a subscription for a gym using this API.


## Permissions

- `gym_subscriptions.delete`: deleting subscriptions for your own gyms
- `gym_subscriptions.delete_any`: deleting subscriptions for any gym

## Response

### 204 No Content
 Deleted successfully

### 404 Not Found
 Invalid gym id or subscription id passed

### 401 Unauthorized
[Authentication error](../../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../../permission-errors.md)
