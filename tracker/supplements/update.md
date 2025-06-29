# `PUT /api/v1/tracker/supplements/{tracker-supplement-id}`
You can update a supplement record in the tracker system using this API.


## Permissions

- `tracker_supplements.update`: updating tracker supplement

## Params

- `tracked_at`: The datetime for the supplement
- `supplement_id`: Id of the supplement
- `notes`: An optional notes

> Are parameters are optional. If you don't pass them, they remain as they are.

## Response

### 200 OK
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
