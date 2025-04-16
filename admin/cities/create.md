# `POST /api/v1/admin/cities/{state}`
This API creates a new city.


## Permissions

- `cities.create`: to create a city

## Params

- `name`: Name of the city (required|maxlength:255)
- ID of the state in the route

## Response

### 201 Created
:
```json
{
    "city": {<city resource>},
}
```

[City Resource](../../resources/city.md)

### 422 Unprocessable Entity
[Validation error](../../validation-errors.md)

### 401 Unauthorized
[Authentication error](../../authentication-errors.md)

### 403 Forbidden
[Permission error](../../permission-errors.md)
