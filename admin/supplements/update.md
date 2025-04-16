# `PUT /api/v1/admin/supplements/{supplement-id}`
You can update an existing supplement using this API.


## Permissions

- `supplements.update`: to update a city

## Params

- `title`: Name of the supplement (required|maxlength:255)
- `link`: A link to website of the supplement (maxlength:255)
- `description`: An optional description for the supplement

All of the parameters are optional. If you don't pass them, they won't get updated.
You still can set them to null if you want.

## Response

### 200 OK

```json
{
    "supplement": {<supplement resource>},
}
```

[Supplement Resource](../../resources/supplement.md)

### 422 Unprocessable Entity
[Validation error](../../validation-errors.md)

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)
