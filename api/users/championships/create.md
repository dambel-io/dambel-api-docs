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
:
```json
<championship resource>
```

[Championship Resource](../../resources/championship.md)

### 422 Unprocessable Entity
[Validation error](../../validation-errors.md)

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)
