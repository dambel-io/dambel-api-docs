# `/api/v1/admin/majors`
This API creates a new major.

- Method: `POST`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions
- `majors.create`: to create a country

### Params

- `title`: Name of the major (required|maxlength:255)

### Response

201:
```json
{
    "major": {<major resource>},
}
```

[Major Resource](../../resources/major.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
