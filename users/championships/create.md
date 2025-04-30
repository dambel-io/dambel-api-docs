# `POST /api/v1/users/{user-id}/championships`
You can create a championship for a user using this API.


## Permissions

- `championships.create`: creating championships for yourself
- `championships.create_any`: creating championships for any user

## Params

- `title`: Title of the championship (maxlength 255)
- `description`: An optional description for the championship (maxlength 2000)
- `date`: Date of the championship (required date format)

## Response

### 201 Created
```json
<championship resource>
```

[Championship Resource](championship_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
