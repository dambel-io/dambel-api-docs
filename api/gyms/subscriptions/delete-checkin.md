# `/api/v1/gyms/{gym-id}/subscriptions/delete-checkin/{subscription-id}/{checkin-id}`
You can delete a checkin on a gym subscription for a gym using this API.

- Method: `DELETE`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions

- `gym_subscription_checkins.delete`: deleting checkins for your own gyms
- `gym_subscription_checkins.delete_any`: deleting checkins for any gym

### Response

204: Deleted successfully

404: Invalid gym id, subscription id, or checkin id passed

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
