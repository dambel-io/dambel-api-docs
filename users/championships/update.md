# `PUT /api/v1/users/{user-id}/championships/{championship-id}`
You can update a championship using this API.


## Permissions

- `championships.update`: update your own championships
- `championships.update_any`: update championships for any user

## Params

- `title`: Title of the championship (maxlength 255)
- `description`: An optional description for the championship (maxlength 2000)
- `date`: Date of the championship (required date format)

All of the parameters are optional. If you don't pass them, they won't get updated.
You still can set them to null if you want.

## Response

### 200 OK

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
