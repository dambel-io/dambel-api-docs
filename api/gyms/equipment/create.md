# `/api/v1/gyms/{gym-id}/equipment`
You can create an equipment for a gym using this API.

- Controller: [`App\Http\Controllers\API\V1\Gyms\Equipment\CreateGymEquipmentController`](../../../../src/app/Http/Controllers/API/V1/Gyms/Equipment\CreateGymEquipmentController.php)
- Method: `POST`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions

- `gym_equipment.create`: creating equipment for your own gyms
- `gym_equipment.create_any`: creating equipment for any gym

### Params

- `equipment_id`: Id of the equipment
- `count`: A numeric value specifying count of the specified equipment in that gym
- `brand_id`: An optional brand ID to specify the brand of the specified equipment
- `description`: An optional description

### Response

201:
```json
<gym equipment resource>
```

[Gym Equipment Resource](../../resources/gym_equipment.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
