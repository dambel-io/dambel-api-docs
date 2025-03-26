# `/api/v1/users/{user-id}/education`
You can create an education for a user using this API.

- Method: `POST`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions

- `education.create`: creating education for yourself
- `education.create_any`: creating education for any user

### Params

- `school`: Name of the school (maxlength 255)
- `field`: Field of the education (maxlength 255)
- `description`: An optional description for the education (maxlength 2000)
- `start_date`: Start date of the education (required date format)
- `end_date`: End date of the education (nullable date format)

### Response

201:
```json
<education resource>
```

[Education Resource](../../resources/education.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
