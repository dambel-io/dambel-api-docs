# POST /api/v1/tracker/wakeups
You can record a wakeup in the tracker system using this API.


## Permissions

- `tracker_wakeups.create`: creating tracker wakeup

## Params

- `tracked_at`: The datetime for the wakeup
- `notes`: An optional notes

## Response

### 201 Created
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
