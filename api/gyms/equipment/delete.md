# `/api/v1/gyms/{gym-id}/equipment/{gym-equipment-id}`
You can delete an equipment from a gym using this API.

- Method: `DELETE`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions

- `gym_equipment.delete`: deleting equipment from their own gyms
- `gym_equipment.delete_any`: deleting equipment of any gym

### Params

No parameter.

### Response

204: No content when equipment gets deleted

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)

404: [Not-found error](../../not-found-errors.md)
