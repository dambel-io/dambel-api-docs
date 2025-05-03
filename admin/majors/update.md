# `PUT /api/v1/admin/majors/{major-id}`
You can update an existing major using this API.


## Permissions

- `majors.view_all`: to access majors
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

[Major Resource](major_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
