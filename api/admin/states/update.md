# `/api/v1/admin/states/{state-id}`
You can update an existing state using this API.

- Method: `PUT`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions
- `states.update`: to update a state

### Params

- `name`: Name of the state (required|maxlength:255)

### Response

200:
```json
{
    "state": {<state resource>},
}
```

[State Resource](../../resources/state.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
