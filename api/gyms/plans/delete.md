# `DELETE /api/v1/gyms/{gym-id}/plans/{plan-id}`
You can delete a subscription plan from a gym using this API.


### Permissions

- `gym_plans.delete`: deleting gym plan from their own gyms
- `gym_plans.delete_any`: deleting gym plan of any gym

### Params

No parameter.

### Response

204: No content when plan gets deleted

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)

404: [Not-found error](../../not-found-errors.md)
