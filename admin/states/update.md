# `PUT /api/v1/admin/states/{state-id}`
You can update an existing state using this API.


## Permissions

- `states.view_all`: to access states
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

[State Resource](state_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
