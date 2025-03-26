# `/api/v1/admin/supplements`
This API creates a new supplement.

- Method: `POST`
- [Requires Authentication](../../auth/login.md#how-to-use-api-token)

### Permissions

- `supplements.create`: to create a supplement

### Params

- `title`: Name of the supplement (required|maxlength:255)
- `link`: A link to a wiki page for the supplement (optional|maxlength:255)
- `description`: An optional description for the supplement

### Response

201:
```json
{
    "supplement": {<supplement resource>},
}
```

[Supplement Resource](../../resources/supplement.md)

422: [Validation error](../../validation-errors.md)

401: [Authentication error](../../authentication-errors.md)

403: [Permission error](../../permission-errors.md)
