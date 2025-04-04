# `GET /api/v1/gyms/{gym-id}/plans`
You can get list of the subscription plans of a gym using this API.


## Permissions

- `gyms.view_any`: is needed if you are trying to read list of plans for an inactive gym or seeing inactive plans

## Params

No parameter.

## Response

### 200 OK

```json
{
    "data": [<gym plan resource>, ...],
}
```

[Gym Plan Resource](../../resources/gym_plan.md)

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)

### 404 Not Found
[Not-found error](../../not-found-errors.md)
