# `POST /api/v1/gyms/{gym-id}/equipment`
You can create an equipment for a gym using this API.


## Permissions

- `gym_equipment.create`: creating equipment for your own gyms
- `gym_equipment.create_any`: creating equipment for any gym

## Params

- `equipment_id`: Id of the equipment
- `count`: A numeric value specifying count of the specified equipment in that gym
- `brand_id`: An optional brand ID to specify the brand of the specified equipment
- `description`: An optional description

## Response

### 201 Created
:
```json
<gym equipment resource>
```

[Gym Equipment Resource](../../resources/gym_equipment.md)

### 422 Unprocessable Entity
[Validation error](../../validation-errors.md)

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)
