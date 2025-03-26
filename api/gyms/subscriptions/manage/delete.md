# `/api/v1/gyms/{gym-id}/subscriptions/manage/{subscription-id}`
You can delete a subscription for a gym using this API.

- Method: `DELETE`
- [Requires Authentication](../../../auth/login.md#how-to-use-api-token)

### Permissions

- `gym_subscriptions.delete`: deleting subscriptions for your own gyms
- `gym_subscriptions.delete_any`: deleting subscriptions for any gym

### Response

204: Deleted successfully

404: Invalid gym id or subscription id passed

401: [Authentication error](../../../authentication-errors.md)

403: [Permission error](../../../permission-errors.md)
