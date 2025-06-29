# `POST /api/v1/tracker/waters`
You can record a water in the tracker system using this API.


## Permissions

- `tracker_waters.create`: creating tracker water

## Params

- `tracked_at`: The datetime for the water
- `glass_count`: Float value for count of glasses
- `notes`: An optional notes

## Response

### 201 Created
```json
<tracker water resource>
```

[Tracker Water Resource](tracker_water_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
