# `PUT /api/v1/users/{user-id}/education/{education-id}`
You can update an education using this API.


## Permissions

- `education.update`: update your own education
- `education.update_any`: update education for any user

## Params

- `school`: Name of the school (maxlength 255)
- `field`: Field of the education (maxlength 255)
- `description`: An optional description for the education (maxlength 2000)
- `start_date`: Start date of the education (required date format)
- `end_date`: End date of the education (nullable date format)

All of the parameters are optional. If you don't pass them, they won't get updated.
You still can set them to null if you want.

## Response

### 200 OK

```json
<education resource>
```

[Education Resource](../../resources/education.md)

### 422 Unprocessable Entity
[Validation error](../../validation-errors.md)

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)
