# `DELETE /api/v1/tracker/sleeps/{tracker-sleep-id}`
You can delete a sleep record in the tracker system using this API.


## Permissions

- `tracker_sleeps.delete`: deleting tracker sleep

## Response

### 204 No Content
Record deleted.

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
