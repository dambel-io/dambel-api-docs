# `POST /api/v1/tracker/weights`
You can record a weight in the tracker system using this API.


## Permissions

- `tracker_weights.create`: creating tracker weight

## Params

- `tracked_at`: The datetime for the weight
- `weight`: Float value for weight (in KG)
- `notes`: An optional notes

## Response

### 201 Created
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
