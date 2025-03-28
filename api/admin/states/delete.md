# `DELETE /api/v1/admin/states/{state-id}`
You can delete a state using this endpoint.


### Permissions
- `states.delete`: to delete any state

### Params

- `replacement_id`: In case the state you are deleting has some data attached to it, you transfer the data to another state by providing it's ID in this optional parameter

### Response

204: No content when state gets deleted

400: When state has data and `replacement_id` is not provided or is not valid. Number of the attached data is returned in `attached_data`≥

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)

404: [Not-found error](../../not-found-errors.md)
