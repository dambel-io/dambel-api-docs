# `PUT /api/v1/gyms/{gym-id}/working-periods/{working-period-id}`
You can update a gym working period using this API.


### Permissions

- `gym_working_periods.update`: update working periods of their own gyms
- `gym_working_periods.update_any`: update working periods for any gym

### Params

- `day`: should be one of these: `saturday`, `sunday`, `monday`, `tuesday`, `wednesday`, `thursday`, `friday`
- `gender`: can be `men`, `women`, or `genderless`
- `opens_at`: the opening time in `H:i` format
- `closes_at`: the closing time in `H:i` format
- `description`: an optional description (maxlength 2000)
- `is_exception`: an optional boolean that specifies if this working period is just for an exceptional date range
- `exception_start_date`: the start date of the exception
- `exception_end_date`: the end date of the exception

All of the parameters are optional. If you don't pass them, they won't get updated.
You still can set them to null if you want.

### Response

200:
```json
<working period resource>
```

[Working Period Resource](../../resources/gym_working_period.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
