# `GET /api/v1/gyms/{gym-id}/working-periods`
You can get list of the working periods of a gym using this API.


## Permissions

- `gyms.view_any`: is needed if you are trying to read list of working periods for an inactive gym

## Params

No parameter.

## Response

### 200 OK

```json
{
    "data": [<working period resource>, ...],
}
```

[Working Period Resource](../../resources/gym_working_period.md)

> NOTE: the list is sorted based on the weekday and opening time

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)

### 404 Not Found
[Not-found error](../../not-found-errors.md)
