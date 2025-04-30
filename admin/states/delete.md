# `DELETE /api/v1/admin/states/{state-id}`
You can delete a state using this endpoint.


## Permissions
- `states.delete`: to delete any state

## Params

- `replacement_id`: In case the state you are deleting has some data attached to it, you transfer the data to another state by providing it's ID in this optional parameter

## Response

### 204 No Content
 No content when state gets deleted

### 400 Bad Request
 When state has data and `replacement_id` is not provided or is not valid. Number of the attached data is returned in `attached_data`≥

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)

### 404 Not Found
[Not-found error](../../_globals/not-found-errors.md)
