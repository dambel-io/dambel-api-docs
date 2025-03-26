# `/api/v1/gyms/{gym-id}`
You can delete a gym using this API (as normal user deleting their own gym and also admin user being able to delete all gyms).

- Controller: [`App\Http\Controllers\API\V1\Gyms\DeleteGymController`](../../../src/app/Http/Controllers/API/V1/Gyms/DeleteGymController.php)
- Method: `DELETE`
- [Requires Authentication](../auth/login.md#how-to-use-api-token)

### Permissions
- `gyms.delete`: to delete your own gym
- `gyms.delete_any`: to delete someone else's gym

### Params

- `id`: ID of the gym in the route

### Response

204: No content when gyms gets deleted

401: [Authentication error](../authentication-errors.md)

403: [Permission error](../permission-errors.md)

404: [Not-found error](../not-found-errors.md)
