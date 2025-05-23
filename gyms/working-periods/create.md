# `POST /api/v1/gyms/{gym-id}/working-periods`
You can create a working period for a gym using this API.


## Permissions

- `gym_working_periods.create`: creating working periods for your own gyms
- `gym_working_periods.create_any`: creating working periods for any gym

## Params

- `day`: should be one of these: `saturday`, `sunday`, `monday`, `tuesday`, `wednesday`, `thursday`, `friday`
- `gender`: can be `men`, `women`, or `genderless`
- `opens_at`: the opening time in `H:i` format
- `closes_at`: the closing time in `H:i` format
- `description`: an optional description (maxlength 2000)
- `is_exception`: an optional boolean that specifies if this working period is just for an exceptional date range
- `exception_start_date`: the start date of the exception
- `exception_end_date`: the end date of the exception

## Response

### 201 Created
```json
<working period resource>
```

[Working Period Resource](gym_working_period_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
