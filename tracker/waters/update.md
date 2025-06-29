# `PUT /api/v1/tracker/waters/{tracker-water-id}`
You can update a water record in the tracker system using this API.


## Permissions

- `tracker_waters.update`: updating tracker water

## Params

- `tracked_at`: The datetime for the water
- `glass_count`: Float value for count of glasses
- `notes`: An optional notes

> Are parameters are optional. If you don't pass them, they remain as they are.

## Response

### 200 OK
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
