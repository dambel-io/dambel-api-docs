# `PUT /api/v1/gyms/{gym-id}/plans/{plan-id}`
You can update a gym plan using this API.


## Permissions

- `gym_plans.update`: update gym plans of their own gyms
- `gym_plans.update_any`: update gym plans for any gym

## Params

- `title`: Title of the plan (maxlength 255)
- `description`: An optional description for the plan (maxlength 2000)
- `price`: Price of the plan (required integer)
- `discount`: Discount percentage (nullable float, default 0)
- `duration_days`: Number of the days that the subscription expires after (optional integer)
- `sessions_count`: Number of the session available in the plan (optional integer)
- `is_active`: A boolean to set active status of plan

NOTE: Either one of `duration_days` and `sessions_count` can be null

All of the parameters are optional. If you don't pass them, they won't get updated.
You still can set them to null if you want.

## Response

### 200 OK

```json
<gym plan resource>
```

[Gym Plan Resource](gym_plan_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
