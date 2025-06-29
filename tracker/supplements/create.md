# `POST /api/v1/tracker/supplements`
You can record a supplement in the tracker system using this API.


## Permissions

- `tracker_supplements.create`: creating tracker supplement

## Params

- `tracked_at`: The datetime for the supplement
- `supplement_id`: Id of the supplement
- `notes`: An optional notes

## Response

### 201 Created
```json
<tracker supplement resource>
```

[Tracker Supplement Resource](tracker_supplement_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
