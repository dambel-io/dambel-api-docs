# PUT /api/v1/tracker/wakeups/{tracker-wakeup-id}
You can update a wakeup record in the tracker system using this API.


## Permissions

- `tracker_wakeups.update`: updating tracker wakeup

## Params

- `tracked_at`: The datetime for the wakeup
- `notes`: An optional notes

> Are parameters are optional. If you don't pass them, they remain as they are.

## Response

### 200 OK
```json
<tracker wakeup resource>
```

[Tracker Wakeup Resource](tracker_wakeup_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
