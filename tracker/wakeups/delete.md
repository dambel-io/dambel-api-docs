# `DELETE /api/v1/tracker/wakeups/{tracker-wakeup-id}`
You can delete a wakeup record in the tracker system using this API.


## Permissions

- `tracker_wakeups.delete`: deleting tracker wakeup

## Response

### 204 No Content
Record deleted.

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
