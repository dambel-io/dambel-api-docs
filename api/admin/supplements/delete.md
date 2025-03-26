# `/api/v1/admin/supplements/{supplement-id}`
You can delete a supplement using this endpoint.

- Method: `DELETE`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions
- `supplements.delete`: to delete any supplement

### Params

- `replacement_id`: In case the supplement you are deleting has some data attached to it, you transfer the data to another supplement by providing it's ID in this optional parameter

### Response

204: No content when supplement gets deleted

400: When supplement has data and `replacement_id` is not provided or is not valid. Number of the attached items is returned in `attached_data`.

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)

404: [Not-found error](../../not-found-errors.md)
