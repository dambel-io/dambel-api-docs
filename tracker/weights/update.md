# `PUT /api/v1/tracker/weights/{tracker-weight-id}`
You can update a weight record in the tracker system using this API.


## Permissions

- `tracker_weights.update`: updating tracker weight

## Params

- `tracked_at`: The datetime for the weight
- `weight`: Float value for weight (in KG)
- `notes`: An optional notes

> Are parameters are optional. If you don't pass them, they remain as they are.

## Response

### 200 OK
```json
<tracker weight resource>
```

[Tracker Weight Resource](tracker_weight_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
