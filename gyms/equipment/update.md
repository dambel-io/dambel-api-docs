# `PUT /api/v1/gyms/{gym-id}/equipment/{equipment-id}`
You can update a gym equipment using this API.


## Permissions

- `gym_equipment.update`: update equipment of their own gyms
- `gym_equipment.update_any`: update equipment for any gym

## Params

- `count`: A numeric value specifying count of the specified equipment in that gym
- `brand_id`: An optional brand ID to specify the brand of the specified equipment
- `description`: An optional description

All of the parameters are optional. If you don't pass them, they won't get updated.
You still can set them to null if you want.

## Response

### 200 OK

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
