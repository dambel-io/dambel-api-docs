# `PUT /api/v1/admin/majors/{major-id}`
You can update an existing major using this API.


## Permissions
- `majors.update`: to update a major

## Params

- `title`: Title of the major (required|maxlength:255)

## Response

### 200 OK

```json
{
    "major": {<major resource>},
}
```

[Major Resource](../../resources/major.md)

### 422 Unprocessable Entity
[Validation error](../../validation-errors.md)

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)
