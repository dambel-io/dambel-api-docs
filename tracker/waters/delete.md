# `DELETE /api/v1/tracker/waters/{tracker-water-id}`
You can delete a water record in the tracker system using this API.


## Permissions

- `tracker_waters.delete`: deleting tracker water

## Response

### 204 No Content
Record deleted.

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
