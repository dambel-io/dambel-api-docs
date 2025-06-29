# `DELETE /api/v1/tracker/supplements/{tracker-supplement-id}`
You can delete a supplement record in the tracker system using this API.


## Permissions

- `tracker_supplements.delete`: deleting tracker supplement

## Response

### 204 No Content
Record deleted.

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
