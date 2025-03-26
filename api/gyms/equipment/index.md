# `/api/v1/gyms/{gym-id}/equipment`
You can get list of the equipment of a gym using this API.

- Controller: [`App\Http\Controllers\API\V1\Gyms\Equipment\ListGymEquipmentController`](../../../../src/app/Http/Controllers/API/V1/Gyms/Equipment\ListGymEquipmentController.php)
- Method: `GET`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions

- `gyms.view_any`: is needed if you are trying to read list of equipment for an inactive gym

### Params

No parameter.

### Response

200:
```json
{
    "data": [<gym equipment resource>, ...],
}
```

[Gym Equipment Resource](../../resources/gym_equipment.md)
