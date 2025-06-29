# `DELETE /api/v1/tracker/weights/{tracker-weight-id}`
You can delete a weight record in the tracker system using this API.


## Permissions

- `tracker_weights.delete`: deleting tracker weight

## Response

### 204 No Content
Record deleted.

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
