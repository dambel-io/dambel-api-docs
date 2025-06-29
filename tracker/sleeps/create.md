# `POST /api/v1/tracker/sleeps`
You can record a sleep in the tracker system using this API.


## Permissions

- `tracker_sleeps.create`: creating tracker sleep

## Params

- `tracked_at`: The datetime for the sleep
- `notes`: An optional notes

## Response

### 201 Created
```json
<tracker sleep resource>
```

[Tracker Sleep Resource](tracker_sleep_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
