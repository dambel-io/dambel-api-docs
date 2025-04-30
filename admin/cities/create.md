# `POST /api/v1/admin/cities/{state}`
This API creates a new city.


## Permissions

- `cities.create`: to create a city

## Params

- `name`: Name of the city (required|maxlength:255)
- ID of the state in the route

## Response

### 201 Created
```json
{
    "city": {<city resource>},
}
```

[City Resource](city_resource.md)

### 422 Unprocessable Entity
[Validation error](../../_globals/validation-errors.md)

### 401 Unauthorized
[Authentication error](../../_globals/authentication-errors.md)

### 403 Forbidden
[Permission error](../../_globals/permission-errors.md)
