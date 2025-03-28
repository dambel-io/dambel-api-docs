# `POST /api/v1/admin/states/{country}`
This API creates a new state.


### Permissions

- `states.create`: to create a state

### Params

- `name`: Name of the state (required|maxlength:255)
- ID of the country in the route

### Response

201:
```json
{
    "state": {<state resource>},
}
```

[State Resource](../../resources/state.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
