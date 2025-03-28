# `PUT /api/v1/admin/states/{state-id}`
You can update an existing state using this API.


## Permissions
- `states.update`: to update a state

## Params

- `name`: Name of the state (required|maxlength:255)

## Response

### 200 OK

```json
{
    "state": {<state resource>},
}
```

[State Resource](../../resources/state.md)

### 422 Unprocessable Entity
 [Validation error](../../validation-errors.md)

### 401 Unauthorized
 [Authentication error](../../authentication-errors.md)

### 403 Forbidden
 [Permission error](../../permission-errors.md)
