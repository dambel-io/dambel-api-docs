# `PUT /api/v1/admin/cities/{city-id}`
You can update an existing city using this API.


## Permissions

- `cities.view_all`: to access cities
- `cities.update`: to update a city

## Params

- `name`: Name of the city (required|maxlength:255)

## Response

### 200 OK

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
